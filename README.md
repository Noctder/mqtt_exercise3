# Proyecto de Monitoreo y Control con ESP32 y MQTT

Este proyecto utiliza un **ESP32** para medir temperatura y humedad con un **sensor DHT22**, mostrar los datos en una **pantalla OLED**, almacenarlos en una **microSD**, y enviarlos a través de **MQTT** a un cliente web.

## Componentes Utilizados
- **ESP32** como microcontrolador
- **Sensor DHT22** para medir temperatura y humedad
- **Pantalla OLED SSD1306** para mostrar información
- **RTC DS1307** para obtener la hora
- **MicroSD** para almacenamiento de datos
- **WiFi y MQTT** para comunicación con un cliente web

---

## Estructura del Proyecto

### 1. **`main.py`** (Código para el ESP32)
Este script se ejecuta en el ESP32 y realiza las siguientes funciones:

#### 📡 **Conectividad**
- Se conecta a una red **WiFi** con las credenciales establecidas.
- Se comunica con un **broker MQTT** para enviar datos y recibir comandos.

#### 🌡️ **Sensado de Datos**
- Lee temperatura y humedad desde el **DHT22**.
- Muestra los valores en la **pantalla OLED**.
- Guarda los datos en un archivo CSV dentro de la **microSD**.

#### 🔁 **Comunicación con MQTT**
- Publica datos en el tópico **`data/temp`**.
- Recibe comandos en el tópico **`data/led`** para encender o apagar un LED conectado al ESP32.

#### 📟 **Pantalla OLED**
- Muestra temperatura y humedad.
- Cambia su visualización según los valores obtenidos (frío, normal o calor).

#### 📁 **Almacenamiento en MicroSD**
- Guarda los datos en un archivo `datalog.csv` en la microSD.
- Si la SD no está disponible, usa la memoria interna.

---

### 2. **`actividad3.html`** (Cliente Web para Visualización)
Esta página web permite visualizar en tiempo real los datos obtenidos por el ESP32.

#### 🎨 **Diseño y Estilos**
- Fondo con gradiente y tarjetas de información.
- Indicadores de **temperatura**, **humedad** y **estado de conexión**.
- Botones para **encender y apagar** un LED a través de MQTT.

#### 📡 **Conectividad con MQTT**
- Se conecta al **broker MQTT `broker.emqx.io`**.
- Se suscribe al tópico **`data/temp`** para recibir los datos.
- Publica mensajes en **`data/led`** para encender/apagar el LED.

#### 🔄 **Interacción Dinámica**
- Actualiza los valores de temperatura y humedad en tiempo real.
- Cambia el estado de conexión dependiendo de la respuesta del servidor MQTT.

---

## 🔧 Instalación y Configuración

### 📥 **Requisitos Previos**
- ESP32 con MicroPython instalado.
- Librerías necesarias en el ESP32: `dht`, `ssd1306`, `ds1307`, `umqtt.simple`, `sdcard`, `network`.
- Un servidor MQTT (se usa **broker.emqx.io** en este caso).

### 📌 **Pasos para ejecutar el proyecto**
1. **Subir `main.py` al ESP32** y ejecutarlo.
2. **Asegurar conexión WiFi** y que el ESP32 esté publicando en MQTT.
3. **Abrir `actividad3.html` en un navegador** para visualizar los datos.
4. **Interactuar con los botones** para encender o apagar el LED de forma remota.

---

## 📌 Posibles Mejoras
✅ Agregar autenticación en MQTT para mayor seguridad.  
✅ Optimizar la frecuencia de envío de datos para reducir consumo de energía.  
✅ Implementar gráficos en la web para visualizar tendencias de temperatura y humedad.

---

## 📩 Contacto
Si tienes dudas o mejoras para el código, siéntete libre de contribuir o contactar a través de GitHub.

---

📌 **Desarrollado por [Tu Nombre]** 🚀

