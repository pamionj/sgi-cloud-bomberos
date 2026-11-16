# SGI 4.ª — Torre de Control Operacional Cloud
### Sistema de Gestión Integral para la 4.ª Compañía de Bomberos de Puente Alto

<p align="center">
  <img src="https://img.shields.io/badge/Versi%C3%B3n-V2.0%20Iterada%20(S12)-c62828?style=for-the-badge&logo=shield" alt="Versión V2.0" />
  <img src="https://img.shields.io/badge/Estado-Prototipo%20Interactivo-15803d?style=for-the-badge&logo=checkmarx" alt="Estado Prototipo" />
  <img src="https://img.shields.io/badge/Arquitectura-Offline--First%20Cloud-0284c7?style=for-the-badge&logo=icloud" alt="Offline-First" />
  <img src="https://img.shields.io/badge/Stack-HTML5%20%7C%20CSS3%20%7C%20Vanilla%20JS-f59e0b?style=for-the-badge&logo=javascript" alt="Stack Tecnológico" />
  <img src="https://img.shields.io/badge/UX%20Design-Design%20Thinking%20%2F%20CdM-7c3aed?style=for-the-badge&logo=figma" alt="Metodología UX" />
  <img src="https://img.shields.io/badge/Instituci%C3%B3n-Cuerpo%20de%20Bomberos%20de%20Puente%20Alto-b91c1c?style=for-the-badge&logo=target" alt="Institución" />
</p>

---

## 📖 Tabla de Contenidos
1. [Descripción General](#-descripción-general)
2. [Propósito y Problema Resuelto](#-propósito-y-problema-resuelto)
3. [Evolución de Versiones (V1.0 vs V2.0)](#-evolución-de-versiones-v10-vs-v20)
4. [Módulos y Funcionalidades Clave](#-módulos-y-funcionalidades-clave)
5. [Metodología de Diseño y Evidencias (Unidad 3)](#-metodología-de-diseño-y-evidencias-unidad-3)
6. [Arquitectura y Tecnologías](#-arquitectura-y-tecnologías)
7. [Estructura del Proyecto](#-estructura-del-proyecto)
8. [Puesta en Marcha / Ejecución](#-puesta-en-marcha--ejecución)
9. [Flujos Operacionales Destacados](#-flujos-operacionales-destacados)
10. [Licencia y Créditos](#-licencia-y-créditos)

---

## 🚒 Descripción General

**SGI 4.ª** es una maqueta interactiva de alta fidelidad diseñada como **Torre de Control Operacional** para la 4.ª Compañía de Bomberos de Puente Alto. El sistema centraliza la respuesta táctica, el estatus de la dotación voluntaria, la trazabilidad de material mayor y menor distribuido en carros bombas y bodega central, la bitácora legal de novedades y la tramitación de oficios con Comandancia.

El prototipo incorpora un conmutador bidireccional en tiempo real entre:
- **V1.0 Inicial (Semana 11)**: *"Torre de Control de Bolsillo"*.
- **V2.0 Iterada (Semana 12)**: *"Torre de Control Todo-Terreno"*, adaptada tras pruebas con usuarios reales (voluntarios, maquinistas y oficiales), incorporando resiliencia sin conectividad, reconocimiento por voz y checklists acelerados para condiciones de emergencia.

---

## 🎯 Propósito y Problema Resuelto

En situaciones de emergencia (incendios estructurales 10-0, rescates vehiculares 10-4 o incidentes con materiales peligrosos HazMat 10-5), la compañía enfrenta tres brechas operativas críticas:
1. **Falta de visibilidad en tiempo real de la dotación disponible**: El personal debe saber al instante si un voluntario o maquinista calificado está en cuartel o en tránsito.
2. **Pérdida de trazabilidad de material e insumos críticos**: Herramientas y consumibles (guantes, mascarillas P100, espumógeno AFFF) dispersos entre 3 carros de emergencia y la bodega central.
3. **Papeleo desconectado y falta de señal en terreno**: Partes de emergencia llenados en papel o sistemas que fallan sin conexión a internet en zonas aisladas o con inhibición de señal.

**SGI 4.ª** resuelve estos desafíos mediante una interfaz visual táctil, de rápida lectura bajo luz diurna o estrés nocturno, compatible con dispositivos móviles y pantallas de sala de guardia.

---

## 🔄 Evolución de Versiones (V1.0 vs V2.0)

El prototipo permite alternar interactivamente entre ambas versiones desde la barra superior:

| Dimensión | V1.0 Inicial (Semana 11) | V2.0 Iterada Post-CDM (Semana 12) |
| :--- | :--- | :--- |
| **Concepto Central** | *Torre de Control de Bolsillo* (Web Centralizada) | *Torre de Control Todo-Terreno* (Resiliente y Táctica) |
| **Conectividad** | Dependiente de conexión a internet constante | **Modo Offline-First** con sincronización automática diferida |
| **Entrada de Datos** | Registro manual mediante teclado/pantalla | **Dictado Manos Libres por Voz** para oficiales y personal en terreno |
| **Revisión de Inventario** | Escaneo QR unitario ítem por ítem | **Checklist Maestro por Gaveta/Compartimento** (< 20 segundos) |
| **Gestión de Stock** | Listado estático de bodega | **Semáforo de Stock Crítico** con alertas automáticas de reposición |
| **Oficios de Comandancia** | Bandeja de entrada visual básica | **Alertas Push Reactivas** y trazabilidad de firmas/resolución |
| **Bajas de Material** | Registro simple | **Baja Auditada** vinculada obligatoriamente a Oficio de Comandancia |

---

## 💻 Módulos y Funcionalidades Clave

```
                               ┌────────────────────────────────────────────────────────┐
                               │           SGI 4.ª — TORRE DE CONTROL CLOUD            │
                               └──────────────────────────┬─────────────────────────────┘
                                                          │
          ┌───────────────────────────┬───────────────────┴───────────────┬──────────────────────────┐
          │                           │                                   │                          │
          ▼                           ▼                                   ▼                          ▼
  👥 GUARDIA EN VIVO       📦 INVENTARIO CUÁDRUPLE             📖 LIBRO DE NOVEDADES       📄 OFICIOS Y BAJAS
  - Semáforo de estados    - 4 Ubicaciones (B-4, S-4, H-4, Bodega)  - Claves 10 (10-0, 10-4...)  - Bandeja Comandancia
  - Actualización 1-touch  - Trazabilidad y Códigos QR          - Descuento de consumibles   - Baja auditada por oficio
  - Monitor de dotación    - Semáforo de Stock Crítico (V2)    - Dictado por voz (V2)       - Notificaciones Push (V2)
                           - Checklist por Gaveta en <20s (V2)  - Modo Offline-First (V2)
```

### 1. 👥 Guardia en Vivo (Disponibilidad en Tiempo Real)
- Monitoreo continuo de la dotación voluntaria (ej. 14 / 22 disponibles).
- Panel rápido interactivo **"Mi Estado de Guardia"**: permuta con un toque entre `Disponible`, `En Emergencia` o `No Disponible`.
- Clasificación de personal por especialidad (Oficial de Guardia, Maquinista, Operativo HazMat, Voluntario).

### 2. 📦 Inventario Cuádruple con Escáner QR
- **Segmentación por ubicación activa**:
  - 🚒 **Carro Bomba B-4** (Material de extinción, mangueras kevlar, hachas pickhead, equipos ERA).
  - 🛠️ **Carro Soporte S-4** (Generadores eléctricos 5kVA, cizallas hidráulicas de rescate vehicular).
  - ☣️ **Carro Químico HazMat H-4** (Detectores multigas 4-en-1, trajes encapsulados Nivel A).
  - 🏭 **Bodega Central** (Insumos médicos, guantes de nitrilo, mascarillas P100, espumógeno AFFF).
- **Escáner QR**: Simulación interactiva de lectura de código QR individual por herramienta y **Checklist Maestro por Gaveta** en V2.0.
- **Semáforo de Reposición (V2.0)**: Indicadores visuales en verde, amarillo y rojo según umbrales mínimos de seguridad.

### 3. 🚒 Libro de Novedades Digital (Bitácora de Incidencias)
- Formulario de despacho conforme a nomenclatura de Bomberos de Chile:
  - `10-0` Incendio Estructural
  - `10-4` Rescate Vehicular
  - `10-5` Incidente HazMat (Fuga de gas / Materiales peligrosos)
  - `10-2` Incendio de Pastizales / Forestal
- Descuento automatizado de consumibles de bodega asociados a la emergencia.
- **Dictado Manos Libres por Voz (V2.0)**: Autocompletado del parte de guardia sin necesidad de teclear.
- **Modo Offline-First (V2.0)**: Almacenamiento local si no hay señal y sincronización al recuperar cobertura con contador de paquetes pendientes.

### 4. 📄 Oficios y Bajas Auditadas
- Control de correspondencia oficial proveniente de Comandancia (`OF-142`, `OF-145`, etc.).
- Ciclo de estados: `Pendiente` ➔ `En Gestión` ➔ `Cerrado`.
- **Módulo de Baja Trazable**: Prohibición de bajas sin asociación a un oficio formal de respaldo, garantizando transparencia patrimonial.

---

## 📊 Metodología de Diseño y Evidencias (Unidad 3)

El prototipo es el resultado de un riguroso proceso de **Diseño Centrado en el Usuario (UCD)** e iteración basada en matrices de evaluación:

| Artefacto / Fase | Archivo de Evidencia | Descripción Metodológica |
| :--- | :--- | :--- |
| **Diagnóstico SQA** | `assets_u3/3_1_1_1_matriz_sqa.png` | Matriz *Lo que Sé, lo que Quiero saber y lo que Aprendí* aplicada al cuartel de bomberos. |
| **Storyboard Inicial** | `assets_u3/3_1_2_1_storyboard_inicial.png` | Narrativa de uso del prototipo inicial durante un llamado nocturno. |
| **Mockup V1.0** | `assets_u3/3_1_2_2_mockup_inicial.png` | Diseño inicial de pantallas para escritorio y tablet de cuartel. |
| **Ficha de Testeo N.° 1** | `assets_u3/3_1_2_3_ficha_testeo_1.png` | Validación de campo con bomberos reales, detectando fricciones de conectividad y usabilidad. |
| **Matriz CdM Inicial** | `assets_u3/3_1_2_4_matriz_cdm_1.png` | Matriz de Criterios de Mérito evaluando viabilidad, deseabilidad y robustez. |
| **Panel de Metáforas Visuales** | `assets_u3/3_1_3_1_panel_metaforas_iterado.png` | Lenguaje de diseño basado en semáforos tácticos, panel de cabina y radios de emergencia. |
| **Storyboard Iterado** | `assets_u3/3_1_3_2_storyboard_iterado.png` | Incorporación del modo offline y dictado por voz durante el retorno del carro bomba. |
| **Mockup Iterado V2.0** | `assets_u3/3_1_3_3_mockup_iterado.png` | Pantallas refinadas con botones grandes para uso con guantes y contrastes altos. |
| **Ficha de Testeo Iteración** | `assets_u3/3_1_3_4_ficha_testeo_iteracion.png` | Verificación de mejoras: tiempo de checklist reducido a < 20s y 0% pérdida de datos sin internet. |
| **Matriz CdM Iterada** | `assets_u3/3_1_2_4_matriz_cdm_iterada.png` | Puntuaciones de mérito posterior a la iteración validando la resolución de cuellos de botella. |
| **Matriz PESTAL Profundizada** | `assets_u3/3_1_4_1_matriz_pestal_profundizada.png` | Análisis contextual Político, Económico, Social, Tecnológico, Ambiental y Legal para el servicio bomberil. |

---

## 🛠️ Arquitectura y Tecnologías

El prototipo fue concebido con principios de **cero dependencias externas pesadas**, garantizando que pueda ejecutarse instantáneamente en cualquier navegador, terminal táctil o dispositivo móvil embebido:

- **HTML5 Semántico**: Estructura accesible con roles claros (`header`, `nav`, `main`, `section`, `table`, `form`).
- **CSS3 Puro**:
  - Variables CSS (`--primary: #c62828`, `--navy: #0f172a`, etc.) para una paleta de color bomberil sobria y funcional.
  - Diseño responsivo mediante CSS Grid y Flexbox adaptable a teléfonos, tablets y monitores de cuartel.
  - Microinteracciones táctiles pensadas para manipulación rápida.
- **JavaScript ES6+ (Vanilla)**:
  - Estado reactivo en memoria para dotación, inventario, novedades y oficios.
  - Simulación del patrón **Offline-First / Local State Reconciliation** para guardar registros en caché local y sincronizarlos cuando la red vuelve a estar disponible.
  - Conmutador dinámico de versión (`v1` / `v2`) mediante clases de raíz (`body.mode-v1` vs `body.mode-v2`).

---

## 📂 Estructura del Proyecto

```text
Bomberos/
├── index.html                       # Prototipo interactivo completo (V1.0 y V2.0)
├── README.md                        # Documentación técnica, metodológica y operativa
└── assets_u3/                       # Evidencias metodológicas de la Unidad 3
    ├── 3_1_1_1_matriz_sqa.png
    ├── 3_1_2_1_storyboard_inicial.png
    ├── 3_1_2_2_mockup_inicial.png
    ├── 3_1_2_3_ficha_testeo_1.png
    ├── 3_1_2_4_matriz_cdm_1.png
    ├── 3_1_2_4_matriz_cdm_iterada.png
    ├── 3_1_3_1_panel_metaforas_iterado.png
    ├── 3_1_3_2_storyboard_iterado.png
    ├── 3_1_3_3_mockup_iterado.png
    ├── 3_1_3_4_ficha_testeo_iteracion.png
    └── 3_1_4_1_matriz_pestal_profundizada.png
```

---

## 🚀 Puesta en Marcha / Ejecución

Al ser un prototipo basado en estándares web abiertos, **no requiere instalación previa de paquetes, Node.js ni compilación**.

### Opción 1: Apertura Directa
1. Descarga o clona el repositorio.
2. Haz doble clic sobre el archivo [index.html](file:///c:/Users/tallerespa/Downloads/Bomberos/index.html) en tu explorador de archivos.
3. Se abrirá de inmediato en tu navegador predeterminado (Google Chrome, Microsoft Edge, Mozilla Firefox o Safari).

### Opción 2: Servidor Local (Recomendado para testing móvil)
Si deseas probar la experiencia táctil desde tu celular en la misma red Wi-Fi:

```bash
# Con Python 3
python -m http.server 8080

# O con npx serve
npx serve .
```
Luego abre `http://localhost:8080` en tu equipo o ingresa la IP local desde tu teléfono.

---

## 📋 Flujos Operacionales Destacados para Probar

1. **Simulación de Respuesta ante Alarma**:
   - Pulsa en la pestaña **1. Guardia en Vivo**.
   - Haz clic en `🚒 Marcarme EN EMERGENCIA` para ver cómo tu voluntario pasa a responder a la guardia.
2. **Revisión de Material y Checklist Express**:
   - Cambia a **V2.0 Iterada** en la esquina superior derecha.
   - Entra en **2. Inventario Cuádruple** y pulsa `⚡ Checklist Rápido por Gaveta`.
   - Revisa el semáforo de reposición de bodega y pulsa `🔔 Notificar Reposición`.
3. **Simulación de Desconexión de Red (Offline-First)**:
   - Activa el botón de conectividad `En línea · Sincronizado` para simular pérdida de señal (`Sin señal · Modo Offline`).
   - Ve a **3. Libro de Novedades**, haz clic en `🎙️ Dictar Parte` y guarda la incidencia.
   - Observa cómo se etiqueta como `Pendiente (Local)`.
   - Vuelve a hacer clic en el botón de señal: el sistema procesará la sincronización en la nube automáticamente y emitirá una alerta.
4. **Auditoría Legal de Bajas**:
   - En **4. Oficios y Bajas**, vincula una herramienta dañada al oficio `OF-142/2026` y confirma la baja auditada.

---

## 📜 Licencia y Créditos

- **Proyecto**: Maqueta Prototipo — Sistema de Gestión Integral de Bomberos (SGI 4.ª).
- **Institución de Referencia**: 4.ª Compañía de Bomberos de Puente Alto.
- **Contexto**: Unidad 3 — Prototipado, Testeo e Iteración de Soluciones Tecnológicas.
- **Licencia**: Uso Académico, Institucional y de Investigación. Se permite su adaptación para cuerpos de bomberos y servicios de emergencia públicos.

<p align="center">
  <b>SGI 4.ª — Al servicio de la comunidad y la seguridad operativa de los bomberos voluntarios.</b>
</p>
