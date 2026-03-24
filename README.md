# Actividad-Managing-IP-Addresses

# 🧩 1. ¿Qué es una dirección IP?

## Tabla

| Concepto | Definición simple | Nivel técnico breve | Ejemplo |
|----------|------------------|--------------------|---------|
| **IP** | Es el "nombre" único que tiene cada dispositivo en una red. Sin él, los datos no saben a dónde ir. | Protocolo de comunicación que asigna una dirección numérica a cada dispositivo. | Tu computador en casa tiene una IP como `192.168.1.5` |
| **IPv4** | La versión original de las direcciones IP. Usa cuatro números separados por puntos (0–255). | Formato de 32 bits que permite ~4 mil millones de direcciones únicas. | `192.168.0.1` |
| **IPv6** | Nuevo sistema con muchísimas más combinaciones. | Formato de 128 bits que permite más de 10³⁸ direcciones únicas. | `2001:0db8:0000:0000:0000:0000:0000:0053` |

---

# ⚙️ 2. Tipos de IP (clave para developers)

- **IP Estática**
  - No cambia.
  - Se usa en servidores.
  - Ideal para producción (APIs, sitios web).

- **IP Dinámica**
  - Cambia periódicamente.
  - Usada en redes domésticas.
  - No importa si cambia.

👉 Como developer:
- Tu servidor necesita **IP estática**.
- Tu casa usa **IP dinámica**.

---

# 💻 3. Conexión directa con desarrollo (CRÍTICO)

## 1. Local vs Producción

### 🔹 En Local (localhost)
- IP: `127.0.0.1`
- Propósito: "Háblate a ti mismo"
- Privacidad: Solo funciona en tu PC

### 🔹 En Producción (Servidor)
- IP pública (ej: `157.240.22.35`)
- Accesible desde cualquier lugar del mundo
- Se usa un dominio (ej: `mi-app.com`) en lugar de la IP

---

## 2. ¿Qué es localhost?

- Es un dominio que siempre apunta a tu propia máquina.
- Ejemplo:
  - Tú → `localhost:3000` → tu PC
  - Tu amigo → `localhost:3000` → su PC

### Compartir tu proyecto local:
- Usar IP privada: `192.168.x.x`
- Estar en la misma red Wi-Fi
- O usar herramientas como **ngrok**

---

## 3. ¿Qué pasa cuando ejecutas `npm run dev`?

1. **Lee el package.json**
   - Busca el script a ejecutar

2. **Asigna un puerto**
   - Ej: 3000, 5173, 8080

3. **Levanta el servidor**
   - Queda escuchando peticiones HTTP

4. **Se vincula a una IP**
   - Por defecto: `127.0.0.1`

⚠️ Errores comunes:
- Puerto ocupado
- Error de código

---

## 4. IP en bases de datos en la nube

- Usan **IP Privada**
- Están dentro de una red cerrada (VPC)
- Solo el backend puede acceder

---

# 🌍 4. Caso práctico real (debugging)

## Escenario:
**“Tu frontend funciona, pero no logra conectarse al backend.”**

---

## ✅ ¿Qué revisar primero?

- URL del backend (IP o dominio)
- Puerto correcto
- Backend encendido
- Configuración de CORS
- Firewall o reglas de red

---

## ❓ ¿Podría ser problema de IP?

### ✔️ Sí, puede ser

El frontend necesita la dirección correcta del backend.

### Casos:

#### 🔹 En Local
- Debe usar: `127.0.0.1:puerto`

#### 🔹 En Producción
- Debe usar:
  - IP pública **o**
  - Dominio

---

## ⚠️ CORS (muy importante)

A veces:
- La IP es correcta ✅
- Pero el backend bloquea la petición ❌

👉 Solución:
- Configurar CORS en el backend para permitir el frontend
