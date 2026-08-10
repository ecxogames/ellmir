## Public and Private Sandbox for Ecxo Registered Products and Services
PP-SERPS, also known as "Public and Private Sandbox for Ecxo Registered Products and Services", is basically a nametag to indentify a software product or service created by us.

## Here is the format of a PP-SERPS nametag:
PP-SERPS-*[PRODUCT_ID]-*[YY.MM]-*[PS-SLUR]

## Here is what each part of the PP-SERPS nametag mean:
**PRODUCT_ID**: (eg. PU/PR.00000.01).
- ***PU/PR**: Part of the id that defines the software as public (PU) or private (PR).*
- ***00000**: The product identifier (A numeric string composed of 5 numbers).*

**01**: The version without the periods (A numeric string composed of 2 to 4 numbers).
**YY.MM**: The date when it was registered.

- ***YY**:* The last numbers of the year (2 digits)
- ***MM**: The current month index (2 digits)*

**PS-SLUR**: Version ID, GitHub commit hash or EBN.
- ***EBN** means Ecxo Binary Number. See the **EBN** note for more.*

## **Here is the list of examples for the usecases of different PP-SERPS registered products:**
2. **PP-SERPS-PR.24560.89-25.08-728xud7j65:** This is the format used by by proprietary softwares used only by a small handful of of people authorized with machine key (Where the PR means Private and the "728xud7j65" is the GitHub commit hash).

2. **PP-SERPS-PU.10180.10-25.09-012:** This is the format used for a public software/service created for the use of the public. The "012" is the version identifier with the periods striped out (0.1.2 is mow 012).

3. **PP-SERPS-PU.10028:** A public software that is only released once and never gets any update. It is easily noticeable since it doesn't have an version number nor a date.

*All the registered pp products (that sounded weird) are indexed on the firebase database under data/indexing/pp_serps. The 🔑 is the pp_serps id number.*