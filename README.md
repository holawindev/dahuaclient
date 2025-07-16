# 📷 DahuaClient – Integración con cámaras Dahua vía API CGI (Digest Auth)

**DahuaClient** es un cliente escrito en **WinDev 2025 SaaS Update 3** para integrarse con cámaras IP Dahua (como la `DH-IPC-HDBW5541R-ASE`) usando su API CGI, permitiendo acceder a datos en tiempo real de **conteo de personas** mediante **autenticación HTTP Digest**.

---

## 🎯 Objetivo

Consultar el resumen estadístico de entradas, salidas y personas presentes desde el endpoint `getSummary` de la API CGI Dahua, cumpliendo con el protocolo de autenticación RFC 7616.

---

## 🛠️ Tecnologías utilizadas

- **WinDev 2025 SaaS Update 3** (necesario para `httpRequest.Authentication = auDigest`)
- HTTP Digest Auth (RFC 7616)
- Cámara Dahua `DH-IPC-HDBW5541R-ASE`
- WLanguage orientado a objetos
- Exportación opcional a JSON local (`C:\Temp`)

---

## 📦 Estructura del proyecto

```
DahuaClient/
├── DahuaAPIClient.wdc             # Clase principal
├── Inicio.wdw                     # Ventana de prueba
├── LICENSE                        # MIT License
├── README.md                      # Este archivo
├── CONTRIBUTING.md                # Guía de contribuciones
├── CODE_OF_CONDUCT.md             # Código de conducta
├── .gitignore                     # Ignora carpetas temporales WinDev
├── DahuaAPI.pdf                   # Documentación original de la API
├── Documentación_DahuaClient.pdf # Manual técnico del proyecto
└── ...
```

---

## 🧪 Ejemplo de uso

```wlanguage
cl_Dahua is DahuaAPIClient("192.168.1.108", "admin")
stResumen is stSummary = cl_Dahua.GetSummary(1, True)

Trace("Personas actualmente dentro: " + stResumen.PersonasAdentro)
```

---

## 📊 Estructura `stSummary`

| Campo             | Descripción                                     |
|------------------|-------------------------------------------------|
| Channel           | Canal de video                                 |
| RuleName          | Tipo de conteo ("NumberStat")                  |
| TotalEntradas     | Ingresos acumulados                            |
| EntradasHoy       | Ingresos en el día actual                      |
| EntradasEstaHora  | Ingresos en la hora actual                     |
| TotalSalidas      | Salidas acumuladas                             |
| SalidasHoy        | Salidas en el día actual                       |
| SalidasEstaHora   | Salidas en la hora actual                      |
| PersonasAdentro   | Personas actualmente dentro del área definida  |

---

## 🔐 Autenticación

La cámara exige **Digest Authentication**, por lo que se utiliza:

```wlanguage
myRequest.Authentication = auDigest
```

Este modo solo está disponible desde **WinDev 2025 SaaS Update 3**.

---

## 🗃 Guardado de JSON (opcional)

Si el segundo parámetro de `GetSummary()` es `True`, se genera un archivo JSON en:

```
C:\Temp\dahua_summary_canalX_YYYYMMDD_HHMMSS.json
```

---

## 📌 Notas

- Por ahora solo se implementa `getSummary`.
- Se puede extender fácilmente a `startFind`, `getDetail`, etc.
- Requiere que el directorio `C:\Temp` exista.

---

## 📚 Documentación incluida

- `Documentación_DahuaClient.pdf`: explica la arquitectura del cliente, estructura de datos, ejemplo de uso y diseño en WinDev.
- `DahuaAPI.pdf`: documentación oficial de la API CGI Dahua, con parámetros y ejemplos de autenticación Digest (RFC 7616).

---

## 🧑‍💻 Autor y comunidad

Proyecto creado para la comunidad **HolaWindev**
🔗 https://holawindev.com
💬 [Discord HolaWindev](https://discord.gg/9xDAJ6ugQr)

---

## 📜 Licencia

Este proyecto se distribuye bajo licencia [MIT](LICENSE).

> ⚠️ *Nota:* Esta integración fue realizada de forma independiente a partir de documentación técnica interna.
> Algunas funciones pueden variar según el modelo, firmware o configuración local de la cámara Dahua.

---

## 🤝 ¿Querés colaborar?

Contribuciones, sugerencias y mejoras son bienvenidas.
Revisá el [CONTRIBUTING.md](CONTRIBUTING.md) y el [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) antes de empezar.

---