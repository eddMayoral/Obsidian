```SQL
CREATE PROC BuscarCampo

(

@busqueda AS VARCHAR(20)

)

AS

BEGIN

select

  t.name as 'Tabla',

  c.name as 'Columna',

  ti.name as 'Tipo',

  c.is_nullable as 'Acepta Datos Nulos',

  c.max_length as 'Largo M�ximo'

from

  sys.tables t left join

  sys.all_columns c on (c.object_id = t.object_id) left join

  sys.types ti on (c.system_type_id = ti.system_type_id)

where

  c.name like '%' + @busqueda + '%' OR

  t.name like '%' + @busqueda + '%'

order by 'tabla'

END
```
#sql