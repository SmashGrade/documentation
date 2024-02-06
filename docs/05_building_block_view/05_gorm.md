# GORM building blocks

GORM is split into two parts:

 - The database provider found in app/provider
 - The entities saved in the database found in app/entity

## Composit keys

Entities that have a composit key (i.e. more than an ID to identify a record) have the autoincrement feature of the ID turned off. This prevents errors at save when only a secondary key other than the ID is changed. But because of this the ID has to be determined manually at creation instead of leaving it empty.