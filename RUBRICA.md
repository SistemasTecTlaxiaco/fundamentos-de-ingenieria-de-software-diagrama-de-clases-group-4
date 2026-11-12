# Rúbrica · Práctica 9 · Diagrama de clases (UML) del módulo del Hub

Fundamentos de Ingeniería de Software (SCC-1007) · Unidad 4 · Modelo de análisis (Sprint 4) · TecNM Campus Tlaxiaco · Docente: José Alfredo Román Cruz · Versión 2, noviembre de 2026

> **Competencia:** elabora el modelo de análisis proyectado en la representación técnica del sistema utilizando la notación orientada a objetos.

**Evidencia:** Diagrama de clases UML del módulo del equipo, construido en Architect a partir del DRS validado en la Unidad 3.  
**Valor:** 30 puntos (30 % de la unidad) · 10 criterios de 3 puntos · por equipo eduScrum, entrega por pull request.

## Qué se entrega

- Un documento de entrega en `entrega/`: PDF, Word (.docx) o Markdown, **con el nombre que quieran** y con la portada que quieran.
- La imagen del diagrama: dentro del documento o como PNG en `docs/analisis/`.
- El proyecto de Architect en `modelo/` (`.qea`).
- La trazabilidad: como tabla dentro del documento **o** en `docs/analisis/trazabilidad.csv`.

El formato es libre: pueden usar la portada del TecNM, ordenar las secciones a su manera y ponerles sus propios títulos. Lo que se califica es que **cada criterio tenga evidencia** en el documento o en el repositorio.

## Requisitos mínimos para ser evaluado

Si falta alguno, la práctica se devuelve sin calificar para que el equipo la corrija antes de la fecha límite.

1. La entrega está **en el repositorio del equipo y entró por pull request**. Un archivo enviado por correo o adjunto en un issue no cuenta.
2. El **.qea abre** en Architect y contiene el diagrama de clases del módulo del propio equipo, no el ejemplo de clase.
3. **Sin datos personales**: ni teléfonos, ni correos, ni CURP, ni firmas escaneadas. A las personas de la organización se les nombra por su cargo, rol o apodo, no por su nombre completo. El repositorio es público.

## Cómo se usa

- Cada criterio vale **3 puntos**. Se elige el nivel que mejor describe el trabajo; si queda entre dos, se asigna el inferior.
- Escala: **Excelente 3.0 · Notable 2.6 · Bueno 2.3 · Suficiente 2.1 · Insuficiente 0**.
- La columna *Indicador* liga cada criterio con los indicadores de alcance A–F de la instrumentación didáctica.
- La calificación es por equipo. Con los pull requests e *Insights › Contributors* el docente puede ajustar el criterio de trabajo en equipo de quien no aportó.

### Cómo leer el comentario del robot

El robot revisa cada pull request y busca la evidencia de cada criterio **sin importar el nombre del archivo ni los títulos**. No califica.

| Marca | Qué significa | ¿Bloquea la fusión? |
|---|---|---|
| ✅ Encontrado | Hay una sección con la evidencia que pide el criterio | No |
| ⚠️ Revisar | Hay evidencia, pero no donde se esperaba; el docente la confirma | No |
| ❌ No encontrado | No hay evidencia del criterio. Ese criterio no puede quedar en Excelente, salvo que el docente la encuentre | No |
| ⛔ Corregir | Falta el documento o el diagrama, o hay datos personales | **Sí** |
| ⏳ Al final | Criterio que se califica al cerrar la práctica (trabajo por pull request) | No |

El robot confirma que la información **existe**; esta rúbrica juzga si está **bien**. Una entrega puede salir toda en ✅ y quedar en Bueno.

## Rúbrica analítica

### 1. Clases identificadas desde el DRS

3 puntos · Indicador A, D

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Cada clase sale de un sustantivo del DRS o de la carrera de sustantivos depurada y usa el vocabulario de la organización. No hay clases inventadas, ni «Sistema», ni clases que en realidad son atributos (como «Fecha»). Cubren todos los RF del módulo. |
| Notable | 2.6 | Clases pertinentes y con el vocabulario de la organización; falta una clase que algún RF necesita, o sobra una. |
| Bueno | 2.3 | Clases pertinentes en su mayoría; faltan o sobran dos, o una es un atributo disfrazado de clase. |
| Suficiente | 2.1 | Clases genéricas o copiadas del ejemplo visto en clase; incluye «Sistema» o una clase por pantalla. |
| Insuficiente | 0 | Menos de cuatro clases, o clases sin relación con el DRS del equipo. |

### 2. Atributos y tipos de datos

3 puntos · Indicador E

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Cada clase tiene los atributos que pide el DRS, con un tipo coherente (kilos: decimal, fecha: Date, estado: enumeración). Ningún atributo repite una relación (no hay «socioId» si ya existe la asociación con Socio). |
| Notable | 2.6 | Atributos completos y con tipo; uno o dos tipos son poco precisos (todo String). |
| Bueno | 2.3 | Atributos pertinentes; varios sin tipo o con tipos incoherentes. |
| Suficiente | 2.1 | Atributos escasos, o que repiten como texto relaciones que deberían ser asociaciones. |
| Insuficiente | 0 | Clases sin atributos. |

### 3. Operaciones ligadas a los requisitos

3 puntos · Indicador D

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Cada operación nace de un verbo de los RF, está en la clase que tiene los datos que usa y se escribe con parámetros y tipo de retorno, por ejemplo registrar(kilos: decimal): Entrega. |
| Notable | 2.6 | Operaciones correctas y bien ubicadas; a algunas les faltan parámetros o tipo de retorno. |
| Bueno | 2.3 | Operaciones pertinentes, pero una o dos están en una clase que no tiene los datos. |
| Suficiente | 2.1 | Solo operaciones genéricas (get, set, guardar(), procesar()) sin relación con los RF. |
| Insuficiente | 0 | Clases sin operaciones. |

### 4. Encapsulamiento y visibilidad

3 puntos · Indicador E

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Atributos privados (−) y operaciones públicas (+) cuando corresponde; usa protegido (#) solo si hay herencia. El equipo justifica cada excepción. |
| Notable | 2.6 | Visibilidad correcta en casi todo; una excepción sin justificar. |
| Bueno | 2.3 | Visibilidad indicada, pero distinta de una clase a otra sin razón. |
| Suficiente | 2.1 | Todo público, o se dejó la visibilidad que pone la herramienta por defecto. |
| Insuficiente | 0 | No se indica visibilidad o el diagrama no la muestra. |

### 5. Asociaciones y multiplicidad

3 puntos · Indicador C, E

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Cada asociación tiene nombre o rol y multiplicidad en los dos extremos, y refleja la regla real de la organización (un socio realiza 0..* entregas; cada entrega es de 1 socio). Sin relaciones sueltas ni duplicadas. |
| Notable | 2.6 | Asociaciones con nombre y multiplicidad completa; una multiplicidad no coincide con lo que dijo la organización. |
| Bueno | 2.3 | Varias asociaciones sin nombre o con multiplicidad en un solo extremo. |
| Suficiente | 2.1 | Líneas sin nombre ni multiplicidad; las relaciones no se pueden leer. |
| Insuficiente | 0 | Clases aisladas, sin relaciones. |

### 6. Agregación, composición y herencia

3 puntos · Indicador C

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Las usa solo cuando el caso lo pide: rombo del lado del todo, composición si la parte no existe sin el todo, herencia con la flecha hacia la clase madre. Si no las necesita, lo justifica por escrito. |
| Notable | 2.6 | Uso correcto; una elección sin justificar (agregación donde bastaba una asociación). |
| Bueno | 2.3 | Un error de notación: rombo del lado equivocado o flecha de herencia invertida. |
| Suficiente | 2.1 | Herencia forzada, o composición donde la parte vive sola; varios errores de notación. |
| Insuficiente | 0 | Relaciones especiales puestas al azar o con notación que no es UML. |

### 7. Trazabilidad con el DRS y el BPMN

3 puntos · Indicador B, D

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Cada clase cita su requisito (RF, RNF o RD) en una nota del modelo, y una tabla de trazabilidad —en el documento o en CSV— cubre todas las clases. Los nombres coinciden con el DRS y con el BPMN mejorado de la Unidad 2. |
| Notable | 2.6 | Trazabilidad completa; uno o dos nombres no coinciden entre el DRS y el diagrama. |
| Bueno | 2.3 | La mayoría de las clases cita requisito; la tabla está incompleta. |
| Suficiente | 2.1 | Solo algunas clases citan requisito; no hay tabla de trazabilidad. |
| Insuficiente | 0 | Sin ninguna trazabilidad hacia los requisitos. |

### 8. Notación UML y uso de Architect

3 puntos · Indicador D

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | El modelo está en el paquete de análisis, en un diagrama de tipo Class, con clases en UpperCamelCase y miembros en lowerCamelCase. El acomodo evita cruces de líneas y la imagen del diagrama se lee bien (en el documento o como PNG de al menos 800 px). |
| Notable | 2.6 | Notación correcta; el acomodo hace difícil leer una parte del diagrama. |
| Bueno | 2.3 | Notación correcta en general; imagen poco legible o nombres escritos de formas distintas. |
| Suficiente | 2.1 | Diagrama hecho con figuras sueltas y no con elementos del modelo. |
| Insuficiente | 0 | Diagrama fuera de Architect (dibujo o foto) o .qea que no abre. |

### 9. Trabajo por pull request

3 puntos · Indicador A, F

> ⏳ **Se califica al final**, cuando el pull request de la entrega ya fue revisado por otro integrante y fusionado. El robot lo muestra como «Al final» y no lo marca como faltante mientras tanto.

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Cada cambio entró por pull request y otro integrante lo revisó con al menos un comentario concreto antes de aprobar. Todos los integrantes aparecen como autores o revisores. El .qea se editó por turnos. |
| Notable | 2.6 | Todo entró por pull request revisado; un integrante no aparece como autor ni como revisor. |
| Bueno | 2.3 | Pull requests aprobados sin descripción, o aprobaciones sin ningún comentario. |
| Suficiente | 2.1 | Un solo pull request grande al final, hecho por una sola persona. |
| Insuficiente | 0 | Entrega fuera del repositorio (correo, adjunto en un issue) o cambios directos a main. |

### 10. Revisión cruzada y mejora

3 puntos · Indicador B, F

| Nivel | Puntos | Descripción |
|---|:---:|---|
| Excelente | 3.0 | Otro equipo revisó el diagrama con esta rúbrica. Cada observación se respondió —en el pull request o en el documento— y se corrigió o se justificó, anotando qué cambió y por qué. |
| Notable | 2.6 | Revisión cruzada atendida; falta anotar qué cambió. |
| Bueno | 2.3 | Hubo revisión cruzada, pero se atendió solo en parte. |
| Suficiente | 2.1 | Se recibió la revisión, sin respuesta ni cambios. |
| Insuficiente | 0 | No hubo revisión cruzada. |

## Dónde buscar la evidencia

| Criterio | Dónde se revisa |
|---|---|
| 1. Clases identificadas desde el DRS | Documento de entrega, DRS y carrera de sustantivos |
| 2. Atributos y tipos de datos | Diagrama y especificación de clases (documento o .qea) |
| 3. Operaciones ligadas a los requisitos | Diagrama, especificación de clases y RF del DRS |
| 4. Encapsulamiento y visibilidad | Diagrama (símbolos − + #) y su justificación |
| 5. Asociaciones y multiplicidad | Diagrama y respuestas de la organización |
| 6. Agregación, composición y herencia | Diagrama y justificación escrita |
| 7. Trazabilidad con el DRS y el BPMN | Notas del modelo y tabla de trazabilidad (documento o CSV) |
| 8. Notación UML y uso de Architect | `modelo/*.qea` e imagen del diagrama |
| 9. Trabajo por pull request | Pestaña *Pull requests* (el robot lista autores y revisores) e *Insights › Contributors* |
| 10. Revisión cruzada y mejora | Comentarios del pull request o sección de revisión del documento |

## Conversión al nivel de desempeño

| Puntos de la rúbrica | Nivel de desempeño | Escala de la instrumentación |
|:---:|:---:|:---:|
| 28.5 – 30.0 | Excelente | 95 – 100 |
| 25.5 – 28.4 | Notable | 85 – 94 |
| 22.5 – 25.4 | Bueno | 75 – 84 |
| 21.0 – 22.4 | Suficiente | 70 – 74 |
| Menos de 21.0 | Insuficiente | NA · competencia no alcanzada |

En Classroom 50, si la tarea está sobre 100, se captura con **Override score** el total × 10 ÷ 3 (por ejemplo, 27 puntos = 90).

## Hoja de calificación

El docente copia esta tabla en un comentario del pull request del equipo (o en el *Feedback pull request* de Classroom 50).

```markdown
| Criterio | Nivel | Puntos | Observación |
|---|---|---:|---|
| 1. Clases identificadas desde el DRS |  | / 3 |  |
| 2. Atributos y tipos de datos |  | / 3 |  |
| 3. Operaciones ligadas a los requisitos |  | / 3 |  |
| 4. Encapsulamiento y visibilidad |  | / 3 |  |
| 5. Asociaciones y multiplicidad |  | / 3 |  |
| 6. Agregación, composición y herencia |  | / 3 |  |
| 7. Trazabilidad con el DRS y el BPMN |  | / 3 |  |
| 8. Notación UML y uso de Architect |  | / 3 |  |
| 9. Trabajo por pull request |  | / 3 |  |
| 10. Revisión cruzada y mejora |  | / 3 |  |
| **Total** |  | **/ 30** |  |

**Lo mejor del trabajo:** 
**Lo primero que deben mejorar:** 
```
