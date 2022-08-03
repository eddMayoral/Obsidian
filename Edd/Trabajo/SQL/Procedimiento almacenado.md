# SQL | PROCEDIMIENTOS EN PL / SQL

  
PL / SQL es un lenguaje estructurado en bloques que permite a los desarrolladores combinar el poder de SQL con declaraciones de procedimiento.  
Un procedimiento almacenado en PL / SQL no es más que una serie de declaraciones SQL declarativas que se pueden almacenar en el catálogo de la base de datos. Se puede pensar en un procedimiento como una función o un método. Se pueden invocar a través de disparadores, otros procedimientos o aplicaciones en Java, PHP, etc.  
Todas las declaraciones de un bloque se pasan al motor de Oracle de una vez, lo que aumenta la velocidad de procesamiento y disminuye el tráfico.

## ¿QUÉ SON LOS PROCEDIMIENTOS ALMACENADOS EN SQL?

**Los procedimientos almacenados** se crean para realizar una o más operaciones DML en la base de datos. No es más que el grupo de sentencias SQL que acepta alguna entrada en forma de parámetros y realiza alguna tarea y puede o no devolver un valor. 

**Ventajas:**

-   Dan como resultado una mejora del rendimiento de la aplicación. Si un procedimiento se llama con frecuencia en una aplicación en una sola conexión, se entrega la versión compilada del procedimiento.
-   Reducen el tráfico entre la base de datos y la aplicación, ya que las declaraciones largas ya se introducen en la base de datos y no es necesario enviarlas una y otra vez a través de la aplicación.
-   Se suman a la reutilización del código, similar a cómo funcionan las funciones y los métodos en otros lenguajes como C / C++ y Java.

**Desventajas:**

-   Los procedimientos almacenados pueden causar un gran uso de memoria. El administrador de la base de datos debe decidir un límite superior en cuanto a cuántos procedimientos almacenados son factibles para una aplicación en particular.
-   MySQL no proporciona la funcionalidad de depurar los procedimientos almacenados.

**Sintaxis para crear un procedimiento almacenado**

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

-- Comments --

CREATE PROCEDURE procedure_name
  = ,
  = ,
  = 

AS
BEGIN
-- Query --
END

GO```




**Sintaxis:** Creación de un procedimiento   
 
```sql
CREATE or REPLACE PROCEDURE name(parameters)
IS
variables;
BEGIN
//statements;
END;```

La parte más importante son los parámetros. Los parámetros se utilizan para pasar valores al procedimiento. Hay 3 tipos diferentes de parámetros, son los siguientes:   
 

1.  **IN:**   
    Este es el parámetro predeterminado para el procedimiento. Siempre recibe los valores del programa de llamada.
2.  **OUT:**   
    Este parámetro siempre envía los valores al programa de llamada.
3.  **IN OUT:**   
    Este parámetro realiza ambas operaciones. Recibe valor y envía los valores al programa que realiza la llamada.
	
	
#sql
