# MCD

- L'association USER <=> ADDRESS est correcte
- L'association USER <=> ORDER est correcte
- L'association ORDER <=> PRODUCT est correcte
- L'association USER <=> Product est incorrecte

Un user peux aimer, 0 ou plusieurs produits (0,n)
Un produit peut être aimé par, 0 ou plusieurs users (0,n)

C'est bien une relation many to many car il n'y a pas de hiérarchie entre les 2 tables.
