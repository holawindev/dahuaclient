# 🤝 Contributing to DahuaClient

¡Gracias por tu interés en contribuir al proyecto **DahuaClient**!  
Este módulo fue creado para facilitar la integración de cámaras Dahua mediante su API CGI utilizando WinDev 2025 SaaS, y puede ser útil para muchos otros desarrolladores de la comunidad HolaWindev.

---

## 📦 Qué puedes contribuir

- 🧠 Mejoras al parsing de respuestas (`GetSummary`, `startFind`, etc.)
- 🔧 Soporte para nuevos endpoints de la API Dahua
- 🐞 Corrección de errores en conexión, autenticación o formato de datos
- 🧪 Agregado de pruebas (manuales o automáticas)
- 📖 Mejoras en la documentación (`README`, comentarios de código, ejemplos)

---

## 📄 Estructura del código

- **`DahuaAPIClient.wdc`**: clase principal. Cada método corresponde a un endpoint (`GetSummary()`, etc.)
- **`Inicio.wdw`**: ventana visual para pruebas con IP/usuario
- **`stSummary`**: estructura utilizada para encapsular los datos
- **JSON opcional**: se guarda automáticamente en `C:\Temp` si se pasa `True` a los métodos

---

## ✅ Buenas prácticas

- Escribe código limpio y documentado (seguimos principios SOLID y Clean Code cuando sea posible).
- Usa nombres claros en español o inglés, pero mantené consistencia.
- Si vas a modificar `DahuaAPIClient`, mantené la clase autocontenida.
- Los métodos públicos deben tener su correspondiente descripción en forma de comentario estándar.

---

## 🧪 Testing

Este proyecto aún no incluye pruebas automatizadas.  
Puedes testear manualmente desde `Inicio.wdw` configurando:

- IP: dirección de la cámara (ej. `192.168.1.108`)
- Usuario: `admin`
- Contraseña: definida en el dispositivo
- Canal: normalmente `1`

---

## 📤 Cómo contribuir

1. **Forkea el repositorio**
2. Crea una rama nueva: `feature/nombre` o `fix/loquesea`
3. Hacé tus cambios y commiteá con mensajes claros
4. Enviá un Pull Request con una breve explicación de lo que hiciste

---

## 📧 Contacto

Si tenés dudas o querés coordinar ideas antes de enviar un PR, podés escribir a:

- ✉️ info@innit.com.uy  
- 💬 [Discord HolaWindev](https://discord.gg/9xDAJ6ugQr)

---

¡Gracias por sumarte! 🚀
