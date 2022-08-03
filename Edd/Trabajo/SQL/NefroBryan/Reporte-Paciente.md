```sql
DECLARE @FechaInicial Date = CURRENT_TIMESTAMP
SELECT CT.[Name] AS "TIPO CONSULTA"
      ,RP.[Name] AS PROTOCOLO
      ,R.[Record_Date] AS CONSULTA
      ,CONCAT(PT.First_Name, PT.Last_Name) AS "NOMBRE PACIENTE"
	  ,PT.Phone1 AS "TELEFONO PACIENTE"
	  , DATEDIFF (YY, PT.Birthday,@FechaInicial) AS EDAD
	  ,PT.Birthday AS CUMPLEAÑOS
	  ,CASE PT.Sex_Id
		WHEN 2 THEN 'F'
		WHEN 1 THEN 'M'
	  END AS "SEXO"
      ,CONCAT(CL.[Name],':',R.Clinic_Other) AS CLINICA
      ,CONCAT(SP1.First_Name,SP1.Last_Name) AS NUTRIOLOGO
	  ,CONCAT(SP2.First_Name,SP2.Last_Name) AS ESPECIALISTA
	  ,SP2.Phone AS "TELEFONO ESPECIALISTA"
      ,[Dialysis_Per_Week] AS "DIALISIS POR SEMANA"
      ,[Meals_Per_Day] AS "COMIDAS AL DIA"
      ,[Collations_Per_Day] "COLACIONES AL DIA"
      ,[Water_Intake] "CONSUMO DE AGUA"
      ,[Concomitant_Diseases_Other] AS "OTRAS ENFERMEDADES"
     ,AP.[Name] AS APETITO
     ,CONCAT(WC.[Name],': ',Who_Cook_Other) AS "QUIEN COCINA"
     ,CASE [Swallowing_Dentition]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Swallowing_Dentition_Notes]
	  END AS "DIFICULTAD AL COMER"
      ,[Common_Dealy_Food_Notes] AS "COMIDA COMUN DIARIA"
      ,ADH.[Name] AS APEGO
      ,UDR.[Name] AS ENTENDIMIENTO
      ,RC.[Name] AS RECEPTIVILIDAD
	  ,CASE [Allergies]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Allergies_Notes]
	  END AS "ALERGIAS"
	  ,CASE [Psychological]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Psychological_Notes]
	  END AS "PSICOLOGICA"
      ,[Breastfeeding_Characteristics] AS "Características de la lactancia materna"
      ,[Ablactation_Characteristics]
	  ,CASE [Change_Medication]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Change_Medication_Notes]
	  END AS "MEDICACION"
      ,[Rec24Notes]
      ,[Biochemical_Notes]
      ,[Diuresis]
	  ,STRING_AGG(ATMT.[Name], ',') AS Antropometria
  FROM [DB_124792_nefrobrain].[medical].[Record] AS R
  INNER JOIN [medical].[Consultation_Type] AS CT ON CT.Id = R.Consultation_Type_Id
  INNER JOIN [medical].[Research_Protocol] AS RP ON RP.Id = R.Research_Protocol_Id
  INNER JOIN [medical].[Patient] AS PT ON PT.Id = R.Patient_Id
  INNER JOIN [medical].[Clinic] AS CL ON CL.Id = R.Clinic_Id
  LEFT JOIN [medical].[Specialist] AS SP1 ON  SP1.Id = R.Nutriologist
  LEFT JOIN [medical].[Specialist] AS SP2 ON  SP2.Id = R.Professional
  INNER JOIN [medical].[Appetite] AS AP ON AP.Id = R.Appetite_Id
  INNER JOIN [medical].[Who_Cook] AS WC ON WC.Id = R.Who_Cook_Id
  LEFT JOIN [medical].[Adherence] AS ADH ON ADH.Id = R.Adherence_Id
  LEFT JOIN [medical].[Understanding] AS UDR ON UDR.Id = R.Understanding_Id
  LEFT JOIN [medical].[Receptibility] AS RC ON RC.Id = R.Recommender_Id
  INNER JOIN [medical].[Anthropometry] AS ATM ON ATM.Record_Id = R.ID
  INNER JOIN [medical].[Anthropometry_Type] AS ATMT ON ATMT.Id = ATM.Anthropometry_Type_Id
  GROUP BY CT.[Name] 
      ,RP.[Name] 
      ,R.[Record_Date] 
      ,CONCAT(PT.First_Name, PT.Last_Name) 
	  ,PT.Phone1
	  , DATEDIFF (YY, PT.Birthday,@FechaInicial) 
	  ,PT.Birthday
	  ,CASE PT.Sex_Id
		WHEN 2 THEN 'F'
		WHEN 1 THEN 'M'
	  END 
      ,CONCAT(CL.[Name],':',R.Clinic_Other) 
      ,CONCAT(SP1.First_Name,SP1.Last_Name)
	  ,CONCAT(SP2.First_Name,SP2.Last_Name) 
	  ,SP2.Phone
      ,[Dialysis_Per_Week] 
      ,[Meals_Per_Day] 
      ,[Collations_Per_Day] 
      ,[Water_Intake] 
      ,[Concomitant_Diseases_Other] 
     ,AP.[Name] 
     ,CONCAT(WC.[Name],': ',Who_Cook_Other) 
     ,CASE [Swallowing_Dentition]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Swallowing_Dentition_Notes]
	  END 
      ,[Common_Dealy_Food_Notes] 
      ,ADH.[Name] 
      ,UDR.[Name] 
      ,RC.[Name] 
	  ,CASE [Allergies]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Allergies_Notes]
	  END 
	  ,CASE [Psychological]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Psychological_Notes]
	  END
      ,[Breastfeeding_Characteristics] 
      ,[Ablactation_Characteristics]
	  ,CASE [Change_Medication]
		WHEN 0 THEN 'NO'
		WHEN 1 THEN [Change_Medication_Notes]
	  END 
      ,[Rec24Notes]
      ,[Biochemical_Notes]
      ,[Diuresis]
```
#sql