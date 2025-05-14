# Laboratorio MyBlog

Este laboratorio pone a prueba la capacidad del alumno para combinar técnicas de enumeración SMB con análisis de contenido web, y aplicar razonamiento lógico para descubrir credenciales. A través de este flujo, los alumnos logran comprender:

- Uso de herramientas como `enum4linux` para enumerar usuarios en sistemas Windows.
- Análisis de pistas dentro de contenido web para deducción de contraseñas.
- Creación de diccionarios personalizados para fuerza bruta dirigida.
- Acceso a recursos compartidos por SMB.
- Acceso posterior a un sitio WordPress con credenciales descubiertas.


## Especificaciones de la máquina 🖥️

- **Sistema:** Windows Server 2016 o 2019
- **Servicios activos:** SMB y Apache (vía XAMPP)
- **Sitio web:** WordPress ubicado en `C:\xampp\htdocs\myblog`
- **Recurso compartido SMB:** `\\<IP>\john`
- **Contenido de la carpeta SMB:** `credentials_wp.txt`
- **Post clave en WordPress:** Entrada donde John menciona haber nacido en un *“año del perro”* (referencia indirecta a 1994).
- **Usuario SMB válido:** `john`  
- **Contraseña esperada:** `1994`
- **Usuario WordPress:** `john`  
- **Contraseña WordPress:** `j0hn_1994`  
- **Flag:** Visible al iniciar sesión como `john` en el panel de administración. 

### Credenciales de la máquina

```bash
nombre: myblog-lab
usuario: administrator
contraseña: 4geeks-lab
```

## Pasos esperados por el alumno

1. **Realiza reconocimiento de red para identificar la máquina**: Utiliza herramientas como `nmap`, `netdiscover` o `enum4linux`. Debe identificar que el host tiene **SMB activo** y servicios web disponibles.


2. **Enumera usuarios con `enum4linux`**. Ejecuta:

    ```bash
    enum4linux -a <IP>
    ```
3. **Explora el sitio WordPress.** Accede a: `http://<IP>/myblog` y lee el blog post donde John menciona el "año del perro".

4. **Crea un diccionario personalizado.** A partir de la pista, deduce que 1994 es el año más probable. Genera el archivo:

    ```bash
    echo 1994 > possible_password.txt
    ```
5. **Ataca el servicio SMB.** Utiliza `smbclient` o `hydra` para autenticarse como **john** con la contraseña 1994. Ejemplo:

    ```bash
    smbclient //192.168.X.X/john -U john
    ```
Accede al recurso compartido y descarga `credentials_wp.txt`.

6. **Accede al WordPress con las credenciales**

    ```text
    Usuario: john
    Contraseña: j0hn_1994
    ```

Accede a:

```perl
http://<IP>/myblog/wp-login.php
```
7. **Encuentra la flag.** La flag se muestra automáticamente en el panel de administración como un mensaje visible.