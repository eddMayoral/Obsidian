```sql
SELECT	CT.[Name] AS "Tipo cliente"
			,CST.[Name] AS "Subtipo cliente"
			,[Loyalty_Program] AS "fecha union"
			,CONCAT(C.[First_Name],C.[Last_Name]) AS "Nombre Cliente"
			,[Birth_Day] AS "Fecha nacimiento"
			,[Phone1] AS Telefono
			,[Phone2] AS "Telefono (otro)"
			,C.[Email] AS Correo
			,S.[Name] AS Sexo
			,RE.[Name] AS "Motivo baja del cliente"
			,SAT.[Name] AS "Tipo de red social"
			,[SocialAccount] AS "Cuenta de red social"
			,[Street] AS Calle
			,[Outdoor] AS "N. Exterior"
			,[Indoor] AS "N. Interior"
			,[Postal_Code] AS CP
			,[Neighborhood] AS Colonia
			,[City] AS Ciudad
			,[State] AS Estado
			,[Country] AS Pais
			,ATT.[Name] AS "Tipo direccion"
			,[Notes] AS Notas
			,E.[Name] AS ARC
			,[Transplant_Wait] AS "Lista traspalnete"
			,[Diabetic]  AS "Diabetico 1(Si) /0 (No)"
			,[Hypertensive] AS "Hipertenso 1(Si) /0 (No)"
			,[Has_Transplant] AS "Tiene trasplante 1(Si) /0 (No)"
			,H.[Name] AS Hospital
			,CONCAT(SS.First_Name,SS.Last_Name) AS "Nombre especialista"
			,SST.[Name] as Especialidad
	  FROM [DB_124792_nefrobrain].[crm].[Client] AS C
	  INNER JOIN [crm].[Client_Type] AS CT ON CT.Id = C.Client_Type_Id
	  INNER JOIN [crm].[Client_SubType] AS CST ON CST.Id = C.Client_SubType_Id
	  LEFT JOIN [crm].[Sex]AS S ON S.Id = C.Sex_Id
	  LEFT JOIN [crm].[Reason_Exit] AS RE ON RE.Id = C.Reason_Exit_Id
	  LEFT JOIN [crm].[Social_Account_Type] AS SAT ON SAT.Id = C.Social_Account_Type_Id
	  INNER JOIN [crm].[Client_Address] AS CA ON CA.ClientId = C.Id
	  INNER JOIN [crm].[Address_Type] AS ATT ON CA.AddressTypeId = ATT.Id
	  LEFT JOIN [crm].[Client_Disease] AS CD ON CD.Client_Id = C.Id
	  LEFT JOIN [crm].[ERC] AS E ON E.Id = CD.ERC_Id
	  LEFT JOIN [crm].[Hospital] AS H ON H.Id = C.Hospital_Id
	  LEFT JOIN [crm].[Specialist] AS SS ON SS.Id = C.Specialist_Id
	  LEFT JOIN [crm].[Specialist_Type] AS SST ON SST.Id = SS.Specialist_Type_Id
```
#sql