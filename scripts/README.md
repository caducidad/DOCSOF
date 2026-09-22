# Scripts

## build_entregable.py

Genera el `.docx` de un entregable a partir de la plantilla y los ficheros `borrador/*.md`.

```bash
python scripts/build_entregable.py \
  entregables/<carpeta> \
  referencias/Plantilla_Entregables_SOFIA.docx \
  entregables/<carpeta>/E3.x.x.docx
```

Requisitos: `python-docx` (`pip install python-docx`).

Las imágenes deben estar en `entregables/<carpeta>/material/capturas/` y referenciadas
en el borrador como `../material/capturas/nombre.png`.

Los `[PENDIENTE: ...]` aparecen en rojo en el Word para identificarlos fácilmente.
