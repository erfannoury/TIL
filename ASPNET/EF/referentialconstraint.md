#Referential Constraint in ADO.NET Data Model EF6

When creating models from using the Entity Framework, you have to define a referential constraint when a two relations are dependent.
To do so, you have to define a Principal entity and Dependent entity.

As you could guess from the names, _Dependent_ entity gets a Foreign Key from the _Principal_ entity.
