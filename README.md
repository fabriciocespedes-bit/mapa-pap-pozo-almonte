# Mapa de calor del público objetivo PAP — Red APS Pozo Almonte

Mapa interactivo de la población objetivo del Programa de Cáncer Cervicouterino: mujeres de 25 a 64 años
inscritas en la red de atención primaria de la comuna de Pozo Almonte. La herramienta se construyó para
decidir dónde emplazar el **PAP móvil**.

**Ver el mapa:** https://USUARIO.github.io/REPOSITORIO/

**Acceso:** la página pide una clave. Solicítela al Departamento de Salud.

---

## Qué muestra

- **Densidad de casos** en cinco clases (bajo · medio bajo · medio · medio alto · alto), sobre callejero o vista satelital.
- **Cobertura de PAP vigente** por localidad, en rojo, naranja, amarillo y verde.
- **Detalle por calle y sector** que se despliega al acercar el mapa sobre una localidad.
- Filtros por estado del PAP, establecimiento, grupo etario y disponibilidad de teléfono.
- Ranking de localidades y sugerencia de recorrido para el móvil.

## Fuente de los datos

| Fuente | Corte | Uso |
|---|---|---|
| Detalle Establecimiento, FONASA | 30-09-2026 | Población inscrita validada y estado de autorización |
| Informe Inscritos / Adscritos, RAYEN | inscripciones desde 01-01-2025 | Dirección, teléfono y sector |
| Informe Población Última Atención, RAYEN | atenciones desde fines de 2021 | Dirección, teléfono y sector |
| Planilla de rescate PAP del programa | octubre 2026 | Fecha del último PAP y vigencia |

Cobertura de la red: CESFAM Pozo Almonte (102303), PSR Mamiña (102403), PSR La Tirana (102406) y PSR La Huayca (102414).
Total: 6.215 mujeres de 25 a 64 años.

## Criterios

- **PAP vigente**: último examen dentro de los últimos tres años.
- **Vencido**: último examen hace más de tres años. **Nunca**: sin registro de PAP. **Sin información**: la planilla no consigna fecha.
- Los grupos de menos de cinco mujeres se marcan como «muestra pequeña» y no se clasifican por cobertura,
  porque con esa cantidad el porcentaje no es interpretable.

## Alcance y limitaciones

- Las cifras son **agregadas**. El sitio no contiene nombres, RUN, teléfonos ni registros individuales.
- Los puntos del mapa están en el **centro de cada localidad**, no en el domicilio de las usuarias.
  Las direcciones de origen son texto sin coordenadas; para una superficie de densidad calle a calle
  habría que geocodificarlas.
- Cinco localidades tienen coordenadas aproximadas por confirmar en terreno: La Huayca, Ex Oficina Victoria,
  Macaya, Parca y Quipisca. El mapa permite arrastrar los puntos y exportar las coordenadas corregidas.
- Solo el 35% de las mujeres tiene dirección registrada en RAYEN, porque ambos informes de origen
  están filtrados por fecha. El detalle por calle describe a ese subconjunto, no al total.

## Acceso y cifrado

El contenido está cifrado con AES-GCM de 256 bits; la clave se deriva de la contraseña con PBKDF2-SHA256
(600.000 iteraciones). Sin la contraseña el archivo no contiene nada legible, tampoco desde el código fuente.

Esto protege frente a la navegación casual y frente a los buscadores. **No equivale a un control de acceso
real**: el archivo cifrado es descargable por cualquiera, y una contraseña corta o predecible puede romperse
sin conexión. Para datos sanitarios se recomienda, además, mantener el repositorio privado.

## Responsable

Departamento de Salud · Ilustre Municipalidad de Pozo Almonte · Región de Tarapacá.
La publicación de estas cifras agregadas fue autorizada por la Dirección de Salud comunal.

## Técnico

Archivo único y autocontenido. Usa [Leaflet](https://leafletjs.com) y leaflet.heat desde CDN, cartografía
de OpenStreetMap y ortofoto de Esri World Imagery. Requiere conexión a internet para el fondo cartográfico;
sin conexión, los indicadores, el ranking y el detalle por calle siguen funcionando.
