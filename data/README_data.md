# Datos de ejemplo para la Tarea · Pentaho PDI

## Archivos
- customers.csv — (Case 1) Clientes con STATE y ZIP para filtrar (e.g., STATE='NY') y ordenar por ZIP.
- products.csv — (Case 2/4) Maestro de productos con Category y ManufacturerID.
- manufacturers.csv — (Case 4) Fabricantes; para join y cálculo de totales/medias por fabricante.
- sales.csv — (Case 2/4) Movimientos de ventas con Units y UnitPrice; Country y fecha.
- logs1.csv, logs2.csv — (Case 3) Registros con nulls en `service`, `level` o `user_id` para practicar filtros compuestos.

## Sugerencias de claves/joins
- Case 2: products.ProductID ↔ sales.ProductID (ordenar ambos streams antes de Merge join).
- Case 4: (Case 2) + products.ManufacturerID ↔ manufacturers.ManufacturerID.

## Notas
- Los datos son sintéticos y reproducibles.
- Fechas en ISO (YYYY-MM-DD). Separador CSV por coma, encoding UTF-8.
