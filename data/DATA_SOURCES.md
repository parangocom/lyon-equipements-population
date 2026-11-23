# Data sources

Both files come from the open data portal of the Métropole de Lyon (https://data.grandlyon.com), retrieved by the authors through the portal's API. The retrieval date and the API endpoint are not recorded.

## Licence

According to the "Conditions d'utilisation" shown on the portal's dataset pages, both datasets are published under the **Licence Ouverte v2.0 (Etalab)**; the "Limite d'utilisation" field is "Non renseigné".

- French: https://data.grandlyon.com/portail/fr/assets/licences/ETALAB-Licence-Ouverte-v2.0.pdf
- English: https://data.grandlyon.com/portail/fr/assets/licences/ETALAB-Licence-Ouverte-v2.0_EN.pdf

This licence requires crediting the source of the information (producer, dataset, date of last update) when the data are reused. Read the licence text for the exact obligations.

| File | Dataset page | Content | Rows (excl. header) |
|---|---|---|---|
| `equipements-publics-metropole-lyon.csv` | https://data.grandlyon.com/portail/fr/jeux-de-donnees/equipements-publics-metropole-lyon/info | Public facilities (theme, type, name, address, commune, INSEE code, coordinates, `datemaj`) | 728 |
| `population-annuelle-communes-metropole-lyon.csv` | (link to add) | Annual population per commune (`pop1876` … `pop2022`), 67 rows including Lyon's arrondissements | 67 |

Source credit: *Métropole de Lyon, data.grandlyon.com, Licence Ouverte v2.0 (Etalab)*.

> **[TO COMPLETE BEFORE PUBLISHING]** Add the population dataset's page URL, confirm the producer of each dataset (the report mentions the Métropole de Lyon and the Ville de Lyon) and the "last update" date shown on each page, then add them to the credit line above.

Both files are `;`-separated, UTF-8 with BOM.

## Modification made for this repository

In `equipements-publics-metropole-lyon.csv`, the columns `tel`, `email` and `web` were removed, because the original contained e-mail addresses that appear to belong to named individuals. The notebook does not use these columns. No row and no other column was changed (checked by comparison with the original file).
