## Ecxo Linking and Indexing Network
To put it in simple words, ELIN is a platform that will allow the management of the Public and Private Sandbox for Ecxo Related Products and Services (PP-SERPS). It will allow the content to be distributed online through various sites with the same design. As of October 2025, the current sites and subdomain sites using ELIN are Ecxo Releases and Ecxo Labs. The registry of will be hosted on the database and will hold the required information about all the required products and services. Every ELIN release and build is identified with an ELIN-UID (ELIN Unique Identifier). Below is the exact format to use when creating an ELIN-UID.

## Agent
As an LLM agent, you must use the ELIN-UID format only when asked to. The ELIN-UID format is used to identify the build and version of various Ecxo related products and services.

## Format
ELIN-[PU/PR]-[BUILD_NUMBER]-[YEAR.MONTH]

## Format Description
- ELIN: This part remains as is...
- PU/PR: PU means public and PR means private.
- BUILD_NUMBER: GitHub commit hash, build and version ids combined like this (09825.10), or timestamp. If none of these, it should be the Project String.
- YEAR.MONTH: The current date written like this (25.10 for 2025-10-24)

## Examples
- ELIN-PU-5htg67.112-26.10
- ELIN-PR-46ghj8.167-26.07