# ELEVATION - Escalando desde lo común hasta el root

En este laboratorio deberás explorar un sistema Linux corporativo con múltiples usuarios, descubrir cuál de ellos puede escalar privilegios y acceder a una flag oculta en el directorio de root. En este laboratorio aprenderás:

- Análisis de archivos internos de usuarios
- Enumeración de cuentas y contraseñas
- Fuerza bruta con diccionario (`rockyou.txt`) usando Hydra
- Escalada de privilegios mediante binarios SUID
- Lectura de flags como usuario root

<how-to-start>
   
## 🌱 Cómo iniciar este laboratorio

Sigue las siguientes instrucciones para comenzar:

1. **Descarga la máquina virtual** desde este [enlace](https://storage.googleapis.com/cybersecurity-machines/elevation-lab.ova).
2. **Importa la máquina** en tu gestor de virtualización preferido (VirtualBox, VMware, etc.).
3. Una vez iniciada la máquina, ¡ya puedes comenzar con el laboratorio!

</how-to-start>


## 📄 Instrucciones

Estás frente a un servidor corporativo con varios usuarios. Tu tarea es descubrir cómo obtener acceso privilegiado a partir de un entorno aparentemente limitado.

1. **Descubre la dirección IP de la máquina ELEVATION.**
   - La máquina está conectada a la misma red que tú, pero su IP no ha sido proporcionada.
   - Utiliza herramientas como `nmap`, `netdiscover` o `arp-scan` para escanear la red.

2. **Accede al sistema vía SSH con usuarios conocidos.**

3. **Presta atención a un usuario sin contraseña conocida.**

4. **Realiza un ataque de fuerza bruta con Hydra.**

5. **Accede y busca formas de escalar privilegios.**

6. **Busca y lee la flag final.**

**Recuerda:** a veces el poder no está en lo visible… sino en lo que parece desprotegido.

¡Feliz hackeo!