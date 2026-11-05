# AleJavVicZei — Digitalización de una empresa de kebab

## 1. Descripción de la pyme

Este proyecto tiene como objetivo digitalizar un restaurante de kebab
mediante la incorporación de soluciones tecnológicas que permitan
optimizar sus procesos operativos, mejorar la gestión del negocio
y ofrecer una mejor experiencia a los clientes.

Se trata de una **pyme** de restauración (establecimiento de kebab)
de carácter local, con un equipo reducido de empleados y un volumen
de negocio concentrado en horas punta (mediodía y noche). Actualmente
el establecimiento trabaja principalmente mediante procesos manuales
y analógicos, lo que genera dificultades en la gestión de pedidos,
la comunicación entre sala y cocina y el control de las operaciones
del negocio.

A través de este proyecto se analizarán las necesidades del
establecimiento y se propondrán soluciones tecnológicas adaptadas
a su situación actual.

## 2. Miembros del equipo y roles

- **Alejandro Cabrero** — Scrum Master.
- **Javier Giménez** — Product Owner.
- **Víctor Puig** — Equipo de Desarrollo.
- **Zeit Warnier** — Equipo de Desarrollo.

## 3. Situación actual del negocio

El restaurante dispone de una infraestructura tecnológica limitada.

### Arquitectura IT

- Utilización de un datáfono para los pagos.
- Caja registradora analógica.
- Gestión manual de pedidos mediante notas manuscritas.
- Ausencia de un sistema informatizado para la gestión del negocio
  y la contabilidad.

### Arquitectura OT

- Termómetros o sensores de temperatura en refrigeradores y frigoríficos.
- Controles de temperatura integrados en freidoras, plancha y horno.
- Ausencia de un registro informatizado de las lecturas de temperatura.

## 4. Problemas detectados (puntos de dolor)

El análisis inicial ha permitido identificar tres áreas principales
de mejora:

### Gestión económica
- Posibles pérdidas económicas derivadas de errores en los pedidos.
- Dificultades para atender la demanda en momentos de máxima afluencia.
- Costes asociados a la impresión y actualización de menús físicos.

### Eficiencia operativa
- Comunicación poco ágil entre sala y cocina.
- Dificultades para organizar y priorizar los pedidos.
- Tiempos de espera difíciles de controlar en horas punta.

### Organización del trabajo
- Sobrecarga del personal en momentos de alta demanda.
- Mayor probabilidad de errores humanos.
- Posible deterioro de la experiencia del cliente.

## 5. Objetivos del proyecto

- Digitalizar los procesos de gestión del restaurante.
- Mejorar la organización y el seguimiento de los pedidos.
- Agilizar la comunicación entre sala y cocina.
- Reducir los errores derivados de los procesos manuales.
- Mejorar la eficiencia operativa en horas punta.
- Facilitar la actualización de los productos y precios.
- Analizar posibles mejoras en el registro y seguimiento
  de las temperaturas de los equipos.

## 6. Metodología de trabajo

El proyecto se desarrollará siguiendo la metodología Scrum,
organizando el trabajo en sprints y distribuyendo las
responsabilidades entre los integrantes del equipo.

## 7. Tecnologías habilitadoras (THD)

| THD | Uso concreto en el negocio | Justificación |
|---|---|---|
| **Web + QR** | Menú digital accesible por QR y sistema de pedidos web desde el móvil del cliente o la tablet de sala. | Elimina costes de impresión y actualización de menús, reduce errores de pedido y agiliza la comunicación sala-cocina. |
| **Cloud (SaaS)** | Almacenamiento de pedidos, ventas, contabilidad y menús en un servicio en la nube. | Evita inversión en servidores propios, permite acceso desde varios dispositivos y facilita copias de seguridad. |
| **IoT** | Sensores de temperatura en frigoríficos y equipos de cocina conectados para registro y avisos automáticos. | Permite detectar temperaturas fuera de rango a tiempo, cumplir la normativa alimentaria y reducir el control manual. |
| **5G** | Conectividad móvil de respaldo y comunicaciones entre dispositivos del local. | Mayor velocidad y baja latencia; sirve como respaldo si falla la conexión fija del establecimiento. |

Cada tecnología se detalla en los documentos enlazados en la sección 11.

## 8. Cloud

La solución se apoya en servicios **en la nube bajo modelo SaaS**:

- **Qué se sube:** pedidos, ventas, contabilidad, menús y registros de temperatura.
- **Por qué:** evita mantener servidores locales, permite acceso desde sala, cocina y administración, y facilita copias de seguridad y actualizaciones automáticas.
- **Modelo:** SaaS para gestión del restaurante y almacenamiento; los datos locales (caja, sensores) se sincronizan periódicamente.

## 9. IA y mapa de datos

### Mapa de datos

| Sistema | Dato que genera | Dónde se guarda | Quién accede | ¿Personal? |
|---|---|---|---|---|
| Datáfono | Importe, fecha, hora y método de pago. | Sistema del proveedor de pagos. | Encargado y proveedor bancario. | Sí, si se puede relacionar con un cliente identificable. |
| Caja registradora | Ventas, importes y movimientos de caja. | Dispositivo local. | Encargado y empleados autorizados. | No, si solo registra datos de ventas. |
| Gestión manual de pedidos | Productos, cantidades, modificaciones y hora del pedido. | Papel (notas manuscritas). | Camareros y cocineros. | No, salvo que incluya datos identificativos del cliente. |
| Sensores de temperatura | Temperatura de frigoríficos y refrigeradores. | Memoria del sensor o dispositivo local. | Encargado y empleados autorizados. | No. |
| Controles de temperatura de maquinaria | Temperaturas de freidoras, plancha y horno. | Memoria o controlador del equipo. | Encargado y empleados autorizados. | No. |

### Inteligencia Artificial

En la fase actual **no se implantará IA**. El volumen de datos y el
grado de digitalización no permiten entrenar modelos fiables, y el
coste no se justifica. A medio plazo se evaluará su uso para:

- **Previsión de demanda** en horas punta a partir del histórico de pedidos.
- **Detección de anomalías** en las temperaturas de los equipos.

## 10. Ciberseguridad

A partir del mapa de datos se han seleccionado los tres riesgos más
importantes y una medida para reducir cada uno.

| Dato | Riesgo | Medida |
|---|---|---|
| Datos de pagos del datáfono | Un acceso no autorizado a la cuenta del proveedor de pagos podría exponer información de las transacciones. | Utilizar un proveedor de pagos fiable, proteger la cuenta con una contraseña segura y activar la verificación en dos pasos. |
| Pedidos del restaurante | Las notas manuscritas podrían perderse, quedar al alcance de personas no autorizadas o contener datos de clientes que se divulguen accidentalmente. | Guardar las notas en un lugar de acceso restringido y destruirlas de forma segura cuando ya no sean necesarias. Si se digitalizan, limitar el acceso mediante cuentas y permisos. |
| Registros de temperatura de frigoríficos y maquinaria | Una avería, una pérdida de registros o una modificación no autorizada podría impedir detectar temperaturas inadecuadas a tiempo. | Restringir quién puede modificar los registros, conservar copias de seguridad y configurar avisos cuando una temperatura salga del rango establecido. |

**Medidas complementarias:**

- **RGPD:** registro de actividades de tratamiento, política de privacidad y atención de los derechos de los interesados.
- **Copias de seguridad** periódicas de pedidos, ventas y registros de temperatura.
- **Control de accesos por roles** con contraseñas robustas y doble factor en cuentas críticas (pagos y administración).
- **Red Wi-Fi segmentada** para clientes y para la gestión del negocio.
- **Formación básica del personal** en buenas prácticas (contraseñas, phishing, manejo seguro de datos).

## 11. Documentación del proyecto

- [Arquitectura IT/OT](ArquitecturasITOT.md)
- [Análisis de puntos de dolor](Pain_Point.md)
- [Mapa de datos](DOCS/MapaDeDatos.md)
- [Riesgos y ciberseguridad](DOCS/CiberseguridadDeLaPyme.md)
- [README](README.md)
- [DIARIO](Diario.md)
- [THD](DOCS/THD)

## 12. Tecnologías utilizadas

[Documento Explicativo](THD_Utilizadas.md)

- [IoT](DOCS/THD/IOT.md)
- [Web + QR](THD_Utilizadas.md)
- [5G](DOCS/THD/5G.md)
- [Nube SaaS](THD_Utilizadas.md)

*No aplica el uso de IA para este negocio en la fase actual (ver sección 9).*

## 13. Conclusión

El proyecto digitaliza los procesos clave del kebab (pedidos, caja,
menús y temperaturas) mediante una solución web con QR, IoT y
servicios en la nube. Esto reduce errores manuales, agiliza la
comunicación sala-cocina y mejora el control operativo, manteniendo
un enfoque de bajo coste y una ciberseguridad proporcionada al riesgo.

Los siguientes pasos son el despliegue del sistema de pedidos y la
integración de los sensores de temperatura con avisos automáticos.

## 14. Estado del proyecto

En desarrollo.
