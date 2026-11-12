# Entrega · Práctica 9

**Equipo:** Grupo 4  
**Módulo del Hub:** Productores y comercialización  
**Organización:** Open Hub Tec · Instituto Tecnológico de Tlaxiaco

## 1. Clases identificadas

Las clases se identificaron a partir de los sustantivos del DRS. El modelo cubre la publicación de productos, los mensajes de compradores, el carrito, la confirmación y seguimiento de pedidos y las solicitudes de asistencia.

| Clase | Sustantivo del DRS | Requisito |
| --- | --- | --- |
| Usuario | Productor, comprador y vendedor | RNF-02; RNF-03 |
| Producto | Ficha de producto | RF-01; RF-02; RF-10 |
| Mensaje | Mensaje escrito o de audio | RF-03; RF-04 |
| Carrito | Carrito de compra | RF-05 |
| ItemCarrito | Producto y cantidad dentro del carrito | RF-05 |
| Pedido | Pedido confirmado | RF-06; RF-07; RF-08; RNF-04 |
| SolicitudSoporte | Solicitud de asistencia | RF-09 |

## 2. Atributos y tipos

Los importes se representan con Decimal. Las enumeraciones limitan los estados y tipos a los valores definidos en el modelo.

| Clase | Atributos y tipos |
| --- | --- |
| Usuario | idUsuario: String, nombre: String, roles: RolUsuario [1..*], credenciales: String |
| Producto | idProducto: String, nombre: String, fotografia: Imagen, precio: Decimal, estado: EstadoProducto |
| Mensaje | idMensaje: String, tipo: TipoMensaje, texto: String, audio: Audio, fecha: Date |
| Carrito | idCarrito: String, fechaCreacion: Date |
| ItemCarrito | cantidad: Integer |
| Pedido | idPedido: String, precio: Decimal, envio: Decimal, comision: Decimal, total: Decimal, estadoCobro: EstadoCobro, estadoEnvio: EstadoEnvio, fecha: Date |
| SolicitudSoporte | folio: String, descripcion: String, fecha: Date |

## 3. Operaciones

Las operaciones representan las acciones de los requisitos. Cada firma indica los parámetros, el tipo de retorno y el requisito asociado.

| Clase | Operación | Requisito |
| --- | --- | --- |
| Usuario | autenticar(credenciales: String): Boolean | RNF-02 |
| Producto | registrar(nombre: String, fotografia: Imagen, precio: Decimal): Producto | RF-01 |
| Producto | cambiarEstado(estado: EstadoProducto): void | RF-02 |
| Producto | consultarActivos(): Lista&lt;Producto&gt; | RF-02 |
| Producto | contarConsultas(inicio: Date, fin: Date): Integer | RF-10 |
| Mensaje | enviar(): void | RF-03; RF-04 |
| Mensaje | reproducirAudio(): void | RF-04 |
| Carrito | agregarProducto(producto: Producto, cantidad: Integer): ItemCarrito | RF-05 |
| Carrito | calcularSubtotal(): Decimal | RF-05 |
| ItemCarrito | subtotal(): Decimal | RF-05 |
| Pedido | confirmar(): void | RF-06 |
| Pedido | calcularTotal(): Decimal | RF-06 |
| Pedido | registrarCobro(estado: EstadoCobro): void | RF-07 |
| Pedido | actualizarEnvio(estado: EstadoEnvio): void | RF-08 |
| SolicitudSoporte | enviar(): String | RF-09 |
| SolicitudSoporte | generarFolio(): String | RF-09 |

## 4. Encapsulamiento y visibilidad

Los atributos son privados (−) para proteger el estado interno de los objetos. Las operaciones son públicas (+) porque los casos de uso las invocan. Por ejemplo, Pedido actualiza su estado de cobro mediante registrarCobro(estado: EstadoCobro).

## 5. Asociaciones y multiplicidad

Cada fila indica cuántas instancias pueden participar en cada extremo. Por ejemplo, un comprador puede realizar 0..* pedidos y cada pedido corresponde a un comprador.

| Clase A | Asociación | Clase B | Multiplicidad A | Multiplicidad B | Regla |
| --- | --- | --- | --- | --- | --- |
| Usuario | publica | Producto | 1 | 0..* | Cada producto lo publica un productor. |
| Usuario | envía | Mensaje | 1 | 0..* | Cada mensaje tiene un remitente. |
| Mensaje | trata de | Producto | 0..* | 1 | Cada mensaje se refiere a un producto. |
| Usuario | posee | Carrito | 1 | 0..1 | Cada carrito pertenece a un comprador. |
| Carrito | contiene | ItemCarrito | 1 | 0..* | Cada ítem pertenece a un carrito. Un carrito puede iniciar vacío. |
| ItemCarrito | corresponde a | Producto | 0..* | 1 | Cada ítem se refiere a un producto. |
| Carrito | origina | Pedido | 1 | 0..1 | Cada pedido se origina en un carrito. |
| Usuario | realiza | Pedido | 1 | 0..* | Cada pedido corresponde a un comprador. |
| Usuario | gestiona | Pedido | 0..1 | 0..* | El modelo admite pedidos sin vendedor asignado. |
| Usuario | solicita | SolicitudSoporte | 1 | 0..* | Cada solicitud pertenece a un usuario. |

## 6. Agregación, composición y herencia

Carrito e ItemCarrito tienen una relación de composición. El rombo relleno se ubica en Carrito porque el ítem pertenece a un carrito y depende de él para existir. Producto se vincula con ItemCarrito por una asociación simple porque el producto puede existir fuera del carrito. Los perfiles de comprador, productor y vendedor se representan como roles de Usuario.

## 7. Trazabilidad

La matriz vincula cada clase con sus requisitos del DRS y las referencias a procesos documentadas para el módulo. Los identificadores P-01 a P-06 corresponden a la numeración usada en el reporte del equipo.

| Clase | Requisito | Proceso | Función del DRS |
| --- | --- | --- | --- |
| Usuario | RNF-02; RNF-03 | Transversal | Control de acceso; Comunicación segura |
| Producto | RF-01; RF-02; RF-10 | P-01; P-02; P-06 | Registrar producto; Consultar catálogo; Consultar estadísticas |
| Mensaje | RF-03; RF-04 | P-03 | Enviar mensaje; Enviar audio |
| Carrito | RF-05 | P-04 | Agregar al carrito |
| ItemCarrito | RF-05 | P-04 | Agregar al carrito |
| Pedido | RF-06; RF-07; RF-08; RNF-04 | P-04; P-05 | Confirmar pedido; Registrar cobro; Actualizar estado de pedido |
| SolicitudSoporte | RF-09 | P-06 | Solicitar asistencia |

## 8. Diagrama y notación UML

El proyecto de Enterprise Architect disponible en la rama se encuentra en [modelo/OpenHub-5BS.eap](../modelo/OpenHub-5BS.eap).

![Diagrama de clases del módulo de productores y comercialización](../docs/analisis/diagrama-clases.png)

## 9. Trabajo en equipo

| Integrante | Pull requests que abrió | Pull requests que revisó |
| --- | --- | --- |
| Giovanna | [#2](https://github.com/SistemasTecTlaxiaco/fundamentos-de-ingenieria-de-software-diagrama-de-clases-group-4/pull/2) | |
| Edwin | | |
| Daniel | | |
| Fernando | | |

## 10. Revisión cruzada

| Observación del equipo revisor | Qué hicimos |
| --- | --- |
| | |
