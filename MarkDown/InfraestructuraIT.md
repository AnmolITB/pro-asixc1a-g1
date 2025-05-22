# Infraestructura Complementaria del CPD

## 1. 🖥️ Servidores

Tendremos un total de **8 servidores** más **2 de reserva**. Cada uno podrá alojar entre **10 y 20 máquinas virtuales**, y el sistema permitirá tener entre **100 y 200 máquinas activas simultáneamente** para los servicios web, bases de datos, correo, etc.

- 🔹 **Modelo**: HPE ProLiant DL380 Gen10  
- 🔹 **RAM**: 128 GB (ampliable)  
- 🔹 **Almacenamiento**: mixto SSD + HDD  
- 🔹 **Red**: 2× NICs por servidor

Cada servidor contará con **2 tarjetas de red (NICs)**:

- 🟦 **NIC 1** → Patch Panel 1 → Switch A  
- 🟥 **NIC 2** → Patch Panel 2 → Switch B  

🔁 Así con todos los servidores, creando una **redundancia activa**: si un switch muere, el tráfico seguirá fluyendo por el otro.

<p align="center">
  <img src="../img/Aservidores.png" alt="Servidores" width="40%" style="border:1px solid #ccc; border-radius:8px;" />
</p>

---

## 2. 🌐 Switches

Usaremos el modelo **Cisco Catalyst 9300**, ya que ofrece mayor soporte y capacidad, incluyendo **VLANs, stacking, redundancia**, entre otras características avanzadas.

- 🧩 **Total**: 6 unidades  
  - 4× switches principales (2 por rack)  
  - 2× switches de backbone (interconexión de racks + dispositivos externos)

🔄 Estarán interconectados en una **topología de anillo** para asegurar redundancia de enlace.

📶 **Distribución de VLANs**:

- VLAN 10: 🧑‍💻 Usuarios  
- VLAN 20: 🛠️ Administración  
- VLAN 30: 💾 Almacenamiento  
- VLAN 40: 📦 Backup

<p align="center">
  <img src="../img/Aswitches.png" alt="Switches" width="40%" style="border:1px solid #ccc; border-radius:8px;" />
</p>

---

## 3. 🧩 Patch Panels

El modelo que utilizaremos será el **Digitus Cat6A**, que soporta velocidades de hasta **10 Gbps** y permite mantener el rack **ordenado, etiquetado y organizado**.

- 🔹 **Total**: 10 paneles de parcheo (24 puertos cada uno)

📌 Distribución:

- 4× interconexión entre servidores y switches  
- 4× conexiones hacia tomas de usuario o puntos WiFi  
- 2× conexión con almacenamiento externo o dispositivos especiales

🔗 Los patch panels actuarán como **punto intermedio** entre servidores/switches y el resto de la instalación, facilitando mantenimiento, trazabilidad y futuras modificaciones.

<p align="center">
  <img src="../img/Apannels.png" alt="Patch Pannels" width="40%" style="border:1px solid #ccc; border-radius:8px;" />
</p>

---

## 4. 🗄️ Racks

El modelo será el **APC AR3150B 42U** (42 unidades de rack = 1,86 metros).

📦 **Distribución**:

- 🟦 **Rack 1**: 5 servidores + switches + paneles  
- 🟥 **Rack 2**: 5 servidores + switches + paneles  
- 🟨 **Rack 3**: Paneles adicionales + switches troncales + almacenamiento + SAI  

⚡ **SAI (UPS)**: proporciona energía temporal cuando se va la luz, usando baterías internas.

- Protege de bajadas de voltaje  
- Permite apagado controlado  
- Evita pérdida/corrupción de datos  

🧩 Esta distribución permite:

- Separar servidores de red troncal  
- Mantener el cableado ordenado  
- Dejar espacio para expansión  
- Facilitar el mantenimiento por secciones

<p align="center">
  <img src="../img/aracks2.png" alt="Racks" width="40%" style="border:1px solid #ccc; border-radius:8px;" />
</p>

---

## 5. 💾 Almacenamiento

Tendremos un sistema **SAN/NAS** conectado por **10 GbE** a los switches, ofreciendo mayor rendimiento que una red estándar.

- ⚙️ **Configuración**: RAID 10  
- 🚀 **Ventajas**: velocidad + redundancia  
- 🧠 Ideal para backups y bases de datos compartidas

<p align="center">
  <img src="../img/AAlmacenamiento.png" alt="Almacenamiento" width="40%" style="border:1px solid #ccc; border-radius:8px;" />
</p>

---

## 🗄️ Resumen General

- 🧠 **Infraestructura principal**: 3 racks de 42U con 10 servidores HPE ProLiant DL380 Gen10 virtualizados.
- 🔀 **Red**: 6 switches Cisco Catalyst 9300 interconectados mediante LACP y organizados con patch panels Cat 6A.
- 💾 **Almacenamiento**: Sistema NAS/SAN conectado a 10GbE, con RAID para alto rendimiento y seguridad.
- 🔄 **Diseño**: Redundante, escalable y optimizado para soportar hasta 8000 usuarios simultáneos sin cuellos de botella.

<p align="center">
  <img src="../img/AResumen.png" alt="Almacenamiento" width="40%" style="border:1px solid #ccc; border-radius:8px;" />
</p>



<p align="center" style="margin-top: 40px;">
  <a href="./ubicacionFisica.md" style="text-decoration: none; margin-right: 20px;">
    <button style="padding: 10px 20px; font-size: 16px; border-radius: 6px; background-color: #2196F3; color: white; border: none;">
      ⬅️ Página anterior
    </button>
  </a>
  
  <a href="../README.md" style="text-decoration: none; margin-right: 20px;">
    <button style="padding: 10px 20px; font-size: 16px; border-radius: 6px; background-color: #2196F3; color: white; border: none;">
      | 🏠 Inicio |
    </button>
  </a>
  
  <a href="./Infraestructuraelectrica.md" style="text-decoration: none; margin-left: 20px;">
    <button style="padding: 10px 20px; font-size: 16px; border-radius: 6px; background-color: #4CAF50; color: white; border: none;">
      Página siguiente ➡️
    </button>
  </a>
</p>





