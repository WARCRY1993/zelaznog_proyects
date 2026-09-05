# Despliegue PoC QR Targa (HMI v6.9)

## Archivos a subir a GitHub Pages (`zelaznog_proyects`)

```
zelaznog_proyects/
├── targa.html                          ← página de destino del QR
└── manuales/
    └── simulazione-di-manuale.pdf      ← manual de ejemplo (simulación)
```

URLs resultantes:

| Recurso | URL |
|---------|-----|
| Targa | `https://warcry1993.github.io/zelaznog_proyects/targa.html` |
| Manual | `https://warcry1993.github.io/zelaznog_proyects/manuales/simulazione-di-manuale.pdf` |

## Pasos

1. En el repo `zelaznog_proyects`, crear carpeta `manuales/`.
2. Subir `simulazione-di-manuale.pdf` (nombre **sin espacios**).
3. Subir `targa.html` en la raíz del repo (o la carpeta que sirva GitHub Pages).
4. Esperar 1–2 min a que Pages publique.
5. Abrir la HMI **v6.9** (`HMI_APP_EG_V_89.html`) en el navegador.
6. Perfil **Admin** → acordeón Administración → verificar:
   - URL base = `https://warcry1993.github.io/zelaznog_proyects/targa.html`
   - URL manual = `https://warcry1993.github.io/zelaznog_proyects/manuales/simulazione-di-manuale.pdf`
7. Completar trazabilidad (al menos **Mixer serial / trzMaquina**) y Pn.
8. Pulsar **QR Targa** → escanear o abrir URL → debe verse la ficha y el botón **Scarica / apri il manuale PDF**.

## Qué quedó implementado en la HMI (v6.9)

- **H1** BASE_URL configurable (Admin + localStorage)
- **H2** manualUrl / rev / lang configurables
- **H3** Payload enriquecido: indirizzo, anno, rpmEje, in, eta, massa, collaudoId, manual*
- **H4** Matrícula desde `trzMaquina` (serial mixer); prompt solo si falta
- **H5** PNG `QR_{matricola}_{fecha}.png`
- **H6** Validación mínima (matrícula, Pn, BASE, manual)
- **H8** Nota PoC visible en modal y en Admin

## Handoff al fabricante

Cambiar en Admin (o valores por defecto en código):

- URL base → `https://manuales.su-dominio.it/targa.html`
- Manual → PDF real del modelo, versionado
- Empresa / dirección

Mantener el mismo contrato de query params (ver `targa_payload_schema_v1.json`).
