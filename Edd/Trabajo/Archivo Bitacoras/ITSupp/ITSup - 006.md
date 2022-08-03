# Motivo
Ajuste de inventario por orden de compra duplicada en Nefrobrain sucursal Oaxaca con folio **OC00018699**
# Solución

Se encontró un posible bug en las ordenes de compra de las sucursales. Aunque ésta esté surtida y cuente con una factura adjunta, Nefrobrain permite la edición de la orden de compra. Con la finalidad de evitar llevar a cabo ajustes de salida de inventario, se provechó la vulnerabilidad para rechazar la entrada del producto y poder cancelar la orden de compra duplicada. Se realizó la descarga de un reporte de inventario antes y después del ajuste tomando de referencia las existencias del SIMBIN RNL 60Caps con lote SB22060301, el cual ya muestra correctamente las piezas físicamente ingresadas