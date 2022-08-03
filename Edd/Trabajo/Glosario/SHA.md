## SHA o SHA1

La función SHA y SHA1 son sinónimos, por lo que hacen el mismo efecto, al igual que MD5 no puede ser revertido y este necesita un campo de 40 caracteres para su almacenamiento, es más seguro que MD5 ya que calcula el cheksum SHA de 160 bits de una cadena, mientras que MD5 la calcula de 128.

**Insertar una contraseña con SHA:**   
```sql
mysql> INSERT INTO usuarios VALUES('usuario',SHA('contraseña'));
```

#encriptado #sql