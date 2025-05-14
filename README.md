# MyBlog - Enumeración y acceso a credenciales expuestas

En este laboratorio deberás explorar un servidor Windows que aloja un sitio WordPress personal y expone un servicio SMB vulnerable. Tu tarea será enumerar usuarios mediante herramientas específicas, analizar pistas dentro del blog, construir tu propio diccionario de contraseñas, acceder a recursos compartidos y obtener una flag secreta. En este laboratorio aprenderás:

- Enumeración de servicios SMB
- Análisis de pistas en contenido web
- Creación de diccionarios personalizados
- Acceso a recursos compartidos en Windows
- Acceso remoto a WordPress con credenciales descubiertas


## 📄 Instrucciones

Estás frente al sitio personal de un fotógrafo llamado **John Wilson**. Además del blog, el servidor expone recursos compartidos por SMB en un entorno Windows. Deberás aplicar técnicas de enumeración y razonamiento para acceder a información sensible.


1. **Descubre la dirección IP de la máquina MyBlog.**
   - La máquina está en tu misma red, pero su IP no ha sido indicada.
   - Utiliza herramientas como `nmap`, `netdiscover` o `enum4linux` para descubrir la dirección IP y servicios activos.

2. **Enumera los usuarios del sistema.**
   - Usa `enum4linux` contra la IP para encontrar posibles usuarios de SMB.
   - Identificarás al usuario `john`.

3. **Explora el blog personal de John.**
   - Accede a la dirección `http://<IP>/myblog` desde tu navegador.
   - Busca un post donde John menciona su año de nacimiento según el horóscopo chino.

4. **Deducción de la contraseña.**
   - A partir del dato del “año del perro”, investiga posibles años: 1994, 1982, etc.
   - Construye un archivo `possible_password.txt` con las opciones razonables.

5. **Realiza un ataque de autenticación SMB.**
   - Usa `hydra` o `smbclient` con tu diccionario para intentar autenticarte como `john`.
   - La contraseña correcta es `1994`.

6. **Accede al recurso compartido.**
   - Conéctate a `\\<IP>\john` y descarga el archivo `credentials_wp.txt`.

7. **Accede al WordPress con las credenciales.**
   - Usuario: `john`
   - Contraseña: `j0hn_1994`
   - Ingresá en `http://<IP>/myblog/wp-login.php`

8. **Captura la flag.**
   - La flag se mostrará directamente en el panel de administración tras iniciar sesión como `john`.

**Consejo:** no todo se resuelve con fuerza bruta. A veces, una pista bien colocada es la clave.

¡Feliz hackeo!

