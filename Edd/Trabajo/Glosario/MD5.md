## #MD5

Para guardar una contraseña encriptada con MD5 necesitaremos una tabla con un campo de 32 caracteres, aunque se ha demostrado que el algoritmo MD5 puede ser vulnerado, la práctica es tan compleja que no merece la pena el esfuerzo, el algoritmo MD5 no puede ser revertido, es decir, no se pueden recuperar contraseñas de este sistema.

**Insertar una contraseña con MD5:**  
```sql
mysql> INSERT INTO usuarios VALUES('usuario',MD5('contraseña'));
```

#encriptado #sql