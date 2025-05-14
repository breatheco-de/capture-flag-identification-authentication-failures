# Enumeración y acceso a credenciales expuestas

En este laboratorio deberás explorar un servidor Windows que aloja un sitio WordPress personal y expone un servicio SMB vulnerable. Tu tarea será enumerar usuarios mediante herramientas específicas, analizar pistas dentro del blog, construir tu propio diccionario de contraseñas, acceder a recursos compartidos y obtener una flag secreta. En este laboratorio aprenderás:

- Enumeración de servicios SMB
- Análisis de pistas en contenido web
- Creación de diccionarios personalizados
- Acceso a recursos compartidos en Windows
- Acceso remoto a WordPress con credenciales descubiertas

<how-to-start>
   
## 🌱 Cómo iniciar este laboratorio

Sigue las siguientes instrucciones para comenzar:

1. **Descarga la máquina virtual** desde este [enlace](https://storage.googleapis.com/cybersecurity-machines/reverse-lab.ova).
2. **Importa la máquina** en tu gestor de virtualización preferido (VirtualBox, VMware, etc.).
3. Una vez iniciada la máquina, ¡ya puedes comenzar con el laboratorio!
</how-to-start>


## 📄 Instrucciones

Estás frente al sitio personal de un fotógrafo llamado **John Wilson**. Además del blog, el servidor expone recursos compartidos por SMB en un entorno Windows. Deberás aplicar técnicas de enumeración y razonamiento para acceder a información sensible.


1. **Descubre la dirección IP de la máquina MyBlog.**: Utiliza herramientas como `nmap`, `netdiscover` o `enum4linux` para descubrir la dirección IP y servicios activos.

2. **Enumera los usuarios del sistema.**: Usa `enum4linux` contra la IP para encontrar posibles usuarios de SMB.

3. **Explora el blog personal.**: Accede a la dirección `http://<IP>/myblog` desde tu navegador.

4. **Deducción de la contraseña.**

5. **Realiza un ataque de autenticación SMB.**: Usa `hydra` o `smbclient` con tu diccionario para intentar autenticarte.

6. **Accede al recurso compartido.**

7. **Accede al WordPress con las credenciales.**

8. **Captura la flag.**: La flag se mostrará directamente en el panel de administración tras iniciar sesión.

**Consejo:** no todo se resuelve con fuerza bruta. A veces, una pista bien colocada es la clave.

¡Feliz hackeo!

