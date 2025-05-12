# Laboratorio ELEVATION

Este laboratorio pone a prueba la capacidad del alumno para identificar usuarios en un sistema Linux, realizar ataques de fuerza bruta con diccionarios y escalar privilegios utilizando un binario vulnerable con permisos SUID.

En este laboratorio los alumnos comprenderán:

- Cómo leer archivos con credenciales internas (sin cifrado)
- Cómo utilizar `hydra` y diccionarios como `rockyou.txt` para ataques de fuerza bruta
- Cómo detectar y explotar binarios con bit SUID
- Cómo ganar acceso root y acceder a archivos sensibles del sistema


## Especificaciones de la máquina 🖥️

- **Sistema:** Ubuntu Server (sin GUI)
- **Servicio activo:** SSH
- **Usuarios definidos:**  
  - `robert` – `P!Roberto1984`  
  - `carla` – `Spring!1994`  
  - `emily` – `1988MoUnt41n`  
  - `daniel` – `@Cal1f0rn!aRulezzZ`  
  - `chester` – contraseña desconocida (pero débil, incluida en `rockyou.txt`)

- **Archivo con credenciales visibles:** `/home/users.txt`
- **Directorio con archivos de relleno:**  
  `/home/Accounting/`, `/home/Financial/`, `/home/Team/`, `/home/HumanResources/`, `/home/Support/`

- **Binario SUID vulnerable:** `/home/chester/rootme`
  - Contenido del binario:
    ```c
    #include <unistd.h>
    int main() {
      setuid(0);
      setgid(0);
      execl("/bin/bash", "bash", NULL);
      return 0;
    }
    ```
  - Compilado como root, con permisos `4755` (SUID)

- **Flag final:** `/root/flag.txt`

> **Nota:** El acceso root solo es posible al descubrir la contraseña de Chester por fuerza bruta y ejecutar el binario con SUID.


### Credenciales de la máquina

```bash
servername: elevation-lab
username: student
password: 4geeks-lab
```
## Pasos esperados por el alumno

1. **Realiza reconocimiento de red para identificar la máquina.**
   - Utiliza herramientas como `nmap`, `netdiscover` o `arp-scan`.
   - Debe detectar una IP con el puerto **22 (SSH)** abierto.

2. **Accede por SSH con los usuarios conocidos.**
   - Inicia sesión como: `robert`, `carla`, `emily` y `daniel`.
   - Verifica que sus carpetas personales contienen solo información irrelevante.

3. **Descubre el archivo `/home/users.txt`.**
   - Contiene las contraseñas de todos los usuarios excepto `chester`.
   - Incluye una advertencia de que la contraseña de Chester es débil.

4. **Realiza un ataque de fuerza bruta con Hydra.**
   - Utiliza el diccionario `rockyou.txt` para encontrar la contraseña de Chester (por ejemplo, `123456` o similar).

5. **Accede al sistema como Chester.**
   - Revisa el contenido del directorio personal de Chester.
   - Encuentra el binario `rootme`, que tiene permisos **SUID**.

6. **Ejecuta el binario vulnerable.**
   - Debería abrir una shell con privilegios de root.

7. **Accede a la flag ubicada en `/root/flag.txt`.**
   - El objetivo es comprender cómo un binario SUID mal configurado puede permitir una escalada completa de privilegios.
