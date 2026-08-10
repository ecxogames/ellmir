## Ecxo Session Token
EST, also know as "Ecxo Session Token" is a string that allows secure authentication when logging in to one of our services.

## **The format of a** EST **is as follow:**
[LOCATION].[TIMESTAMP].[IP]

# Here is what each part of the UIC mean:
**[**LOCATION**].[**TIMESTAMP**]**.[IP]: (eg. CA.1780062683454.27.283.293.29).

- *LOCATION: Product Tag, eg. ECXO for ecxo interactive.*
- *TIMESTAMP: The date and time (in javascript Date.now()) timestamp.*
- IP: IP Adress where the login was registered


```javascript

/**
 * Ecxo Session Token metadata.
 *
 * Format: [PRODUCT_TAG].[TIMESTAMP].[IP]
 * Example: ECXO.1780062683454.27.283.293.29
 *
 * An EST contains predictable metadata and is not an authentication secret on
 * its own. Authentication should additionally use a cryptographically random,
 * server-validated session credential.
 */
const API_URL = "https://api.ecxogames.ca";

/**
 * Helper for making API requests.
 */
async function request(endpoint, options = {}) {
    const response = await fetch(`${API_URL}${endpoint}`, options);

    if (!response.ok) {
        throw new Error(`API request failed with status ${response.status}.`);
    }

    const content_type = response.headers.get("content-type");
    if (content_type && content_type.includes("application/json")) {
        return response.json();
    }

    return response;
}

export const IP = {
    /**
     * Get the client's public IP address.
     * @returns {Promise<string>}
     */
    GET: async () => {
        const data = await request("/ip");
        return data.ip || data;
    }
};

export class EST {
    static async Generate(location) {
        const clean_location = this.FormatLocation(location);
        const timestamp = Date.now();
        const ip = await this.GetIP();

        return `${clean_location}.${timestamp}.${ip}`;
    }

    static async GetIP() {
        const ip = await IP.GET();

        if (typeof ip !== "string" || !ip.trim()) {
            throw new Error("IP address was not returned by the API.");
        }

        return ip.trim();
    }

    static FormatLocation(location) {
        if (typeof location !== "string") {
            throw new Error("Location must be a valid product tag.");
        }

        const product_tag = location.trim().toUpperCase();

        if (!/^[A-Z0-9_-]{1,32}$/.test(product_tag)) {
            throw new Error("Location must be a 1-32 character product tag.");
        }

        return product_tag;
    }

    static Parse(token) {
        if (typeof token !== "string") {
            throw new Error("Invalid EST format.");
        }

        const first_separator = token.indexOf(".");
        const second_separator = token.indexOf(".", first_separator + 1);

        if (first_separator <= 0 || second_separator <= first_separator + 1) {
            throw new Error("Invalid EST format.");
        }

        const location = token.slice(0, first_separator);
        const timestamp_text = token.slice(first_separator + 1, second_separator);
        const ip = token.slice(second_separator + 1);
        const timestamp = Number(timestamp_text);

        if (this.FormatLocation(location) !== location ||
            !/^\d+$/.test(timestamp_text) ||
            !Number.isSafeInteger(timestamp) ||
            timestamp < 0 ||
            !ip ||
            /\s/.test(ip)) {
            throw new Error("Invalid EST format.");
        }

        return {
            Location: location,
            Timestamp: timestamp,
            IP: ip
        };
    }

    static IsExpired(token, max_age_ms) {
        if (!Number.isFinite(max_age_ms) || max_age_ms < 0) {
            throw new Error("Maximum age must be a non-negative number.");
        }

        const parsed_token = this.Parse(token);
        return Date.now() - parsed_token.Timestamp > max_age_ms;
    }
}
```