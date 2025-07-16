# 📷 DahuaClient – Integración con cámaras Dahua vía API CGI (Digest Auth)

Este proyecto implementa un cliente en **WinDev 2025 SaaS Update 3** para conectarse a cámaras Dahua IP que soportan **API CGI** y recuperar datos de **conteo de personas** mediante **autenticación HTTP Digest**.

---

## 🎯 Objetivo

Obtener estadísticas en tiempo real (entradas, salidas y personas presentes) desde cámaras Dahua, utilizando la función `getSummary` de su API CGI.

---

## 🛠️ Tecnologías utilizadas

- 🔧 **WinDev 2025 SaaS Update 3** (requerido por `httpRequest.Authentication = auDigest`)
- 🌐 HTTP Digest Auth (RFC 7616)
- 📷 Cámara Dahua `DH-IPC-HDBW5541R-ASE`
- 🧠 Diseño modular: clase `DahuaAPIClient`
- 🗂 Guardado opcional en JSON (`C:\Temp\dahua_summary_canalX_fecha.json`)

---

## 📦 Estructura del proyecto

```
DahuaClient/
├── DahuaAPIClient.wdc          # Clase principal de integración
├── Inicio.wdw                  # Ventana para ingresar IP y usuario
├── LICENSE
├── README.md
├── Documentación_DahuaClient.pdf
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

## 📊 Estructura de datos `stSummary`

| Campo              | Descripción                                      |
|-------------------|--------------------------------------------------|
| Channel            | Canal de video                                    |
| RuleName           | Tipo de regla (ej: `"NumberStat"`)               |
| TotalEntradas      | Total de personas que ingresaron históricamente  |
| EntradasHoy        | Entradas en el día actual                        |
| EntradasEstaHora   | Entradas en la hora actual                       |
| TotalSalidas       | Total de salidas históricas                      |
| SalidasHoy         | Salidas del día actual                           |
| SalidasEstaHora    | Salidas en la hora actual                        |
| PersonasAdentro    | Personas detectadas actualmente en el área       |

---

## 🔐 Requisitos para autenticación

La cámara requiere **Digest Authentication** según RFC 7616.

En `WinDev 2025 SaaS Update 3`, se habilita mediante:

```wlanguage
myRequest.Authentication = auDigest
```

El método `GetSummary()` configura automáticamente el objeto `httpRequest` con esta opción.

---

## 📁 Guardado de datos JSON (opcional)

Si `bSaveJSON = True`, los datos obtenidos se guardan en:

```
C:\Temp\dahua_summary_canalX_YYYYMMDD_HHMMSS.json
```

Incluye:

- Timestamp
- IP
- Canal
- Totales de entradas/salidas
- Personas adentro

---

## 📌 Observaciones

- Actualmente solo implementa `getSummary`, pero está diseñada para ampliarse fácilmente.
- Requiere que `C:\Temp` exista para guardar los archivos JSON.
- Soporta múltiples canales (argumento en `GetSummary()`).

---

## 📄 Documentación incluida

- `Documentación_DahuaClient.pdf`: detalles del diseño de clases, interfaz WinDev, parsing, guardado y arquitectura del proyecto.

---

## 🤝 Autor

Desarrollado por **Juan Barbat (InnIT)**
🌐 https://innit.com.uy
💬 Comunidad: [Discord HolaWindev](https://discord.gg/9xDAJ6ugQr)

---

## 🛡️ Licencia

Este proyecto es de uso privado. La integración con cámaras Dahua no está oficialmente soportada por el fabricante. Usar bajo tu propio criterio y respetando las condiciones del entorno donde se implemente.
