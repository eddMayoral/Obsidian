# Motivo
Ajuste de inventario por orden de compra duplicada en Nefrobrain sucursal Oaxaca con folio **OC00018699**
# Solución

Dado a un error del cual no fue posible determinar su origen en las ordenes de compra de las sucursales. Para poder determinar una posible solucion se realizo un backup de la BD la cual fue montada en localhost asi como el proyecto de NefroBrain para ejecutar las pruebas necesarias sin afectar el entrorno productivo, esto nos permitio entrontrar una vulnerabilidad dentro del sistema, la cual fue explotada para evitar realizar ajustes de inventario la cual permite el modificar la orden y asi restablecer las cantidades adecuadas de mercancia ingresada fisicamete, se extrae un reporte de inventario antes y después de dicho movimiento para validar la resolucion