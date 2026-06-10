# Cultivo en Agar de Mixomicetos (Semi-axénico)

🌐 [English](agar-culture.md)

**Última actualización:** junio 2026  
**Referencia:** Molina-Viramontes et al. (2025). https://doi.org/10.1111/jeu.70058

---

## Propósito

Cultivo semi-axénico de plasmodios de mixomicetos a partir de esporoforos de cámara húmeda en medios de cultivo estériles. Este proceso reduce progresivamente la contaminación bacteriana, dando lugar a plasmodios con una microbiota alterada (**estado de axenización / disbiosis**). Los esporoforos obtenidos por este método se denominan **Esporocarpos Axenizados (ASp)**.

Los ASp son el material de partida para los experimentos de extracción de ADN que comparan los estados de eubiosis y disbiosis del microbioma del plasmodio.

---

## Materiales

- Cajas de Petri (90 mm)
- Pinzas estériles
- Bisturí estéril
- Estereomicroscopio (p. ej., OLYMPUS SZX7)
- Autoclave
- Medios de cultivo (ver más abajo)
- Hojuelas de avena estériles o avena molida (*Avena sativa*)
- Esporocarpos de Cámara Húmeda (MCSp) — ver [protocolo de Cultivo en Cámara Húmeda](moist-chamber-culture_es.md)

---

## Medios de Cultivo

Todos los medios se esterilizan en autoclave a **120 °C durante 15 min**.

| Abreviatura | Nombre | Composición |
|---|---|---|
| **WA+** ⭐ | Agar agua + avena | 500 mL de agua destilada + 7.5 g de agar bacteriológico. Tras la inoculación, agregar hojuelas de avena estériles o avena molida estéril. |
| WA | Agar agua | 500 mL de agua destilada + 7.5 g de agar bacteriológico |
| OA | Agar avena | Formulación estándar de agar avena |
| LA | Agar de hojarasca | Preparado a partir de extracto de hojarasca de campo |
| LOA | Agar de hojarasca + avena | Extracto de hojarasca + avena |

> ⭐ **Se recomienda WA+.** En nuestras condiciones produjo el mejor crecimiento de plasmodio con el menor crecimiento de contaminantes entre todos los medios probados.

---

## Protocolo

### Inoculación con Esporas

1. Bajo el estereomicroscopio, recoger MCSp individuales con pinzas estériles.
2. Triturar los esporocarpos e inocular las esporas en cajas de Petri con el medio de cultivo estéril.
3. Incubar en **oscuridad a temperatura ambiente (18–22 °C)**.
4. Revisar periódicamente con iluminación por transmisión para detectar crecimiento del plasmodio.

### Descontaminación

5. Una vez que el plasmodio crezca, identificar las secciones sin contaminación.
6. Cortar secciones de plasmodio limpio con agar usando un bisturí estéril.
7. Transferir al centro de una nueva caja de Petri con el mismo medio.
8. Repetir hasta que no sean visibles contaminantes en el medio.

### Inducción de Esporulación

9. Permitir que el plasmodio crezca sin agregar más nutrientes para inducir la esporulación en condiciones secas y oscuras.
10. Cosechar los ASp para análisis moleculares.

---

## Extracción de ADN (de plasmodios)

Los plasmodios deben muestrearse cuando alcancen al menos **5 cm de diámetro**. Muestrear desde el frente de crecimiento (venas primarias y secundarias) para la extracción de ADN.

Se han validado dos métodos de extracción (Molina-Viramontes et al. 2025):

### Método comercial (recomendado para estudios de diversidad)
- **Kit:** DNeasy PowerSoil (Qiagen, Alemania)
- Seguir las instrucciones del fabricante.
- Recupera mayor diversidad taxonómica, especialmente Actinomycetota.
- El ADN es estable hasta **2 días** a −20 °C.

### Método no comercial (recomendado para recuperación de Gram-negativos y mayor estabilidad del ADN)
1. Tratar los plasmodios con EDTA 100 mM (pH 8) + lisozima (10 mg/mL) a 37 °C durante 1 h.
2. Lisar con SDS y proteinasa K a 60 °C.
3. Ruptura mecánica con arena estéril y homogeneizador FastPrep.
4. Purificar por precipitación diferencial y extracción con fenol-cloroformo-alcohol isoamílico.
5. Precipitar con polietilenglicol, lavar con etanol y resuspender en agua grado biología molecular.
6. Agregar fenol para prevenir la degradación del ADN: extiende la estabilidad a **>12 días** a −20 °C.
7. Evaluar pureza e integridad por electroforesis en gel de agarosa al 1%. Incluir blancos de reactivos.

> ⚠️ El manejo de fenol requiere campana de extracción adecuada e infraestructura para disposición de solventes.

---

## Secuenciación de Amplicones de ARNr 16S

Amplificar las regiones hipervariables V3–V4 con primers indexados:

| Primer | Secuencia (5'→3') |
|--------|------------------|
| 341F | `CCTACGGGNGGCWGCAG` |
| 805R | `GACTACHVGGGTATCTAATCC` |

- Seguir el protocolo de amplificación de Montoya-Ciriaco et al. (2020). DOI: [10.1186/s40168-020-0783-6](https://doi.org/10.1186/s40168-020-0783-6)
- Purificar por triplicado los productos de PCR de indexado en gel de agarosa al 2%.
- Cuantificar con el ensayo Quant-iT PicoGreen dsDNA (fluorómetro NanoDrop 3300).
- Normalizar, mezclar en cantidades equimolares y secuenciar en Illumina MiSeq (paired-end 300 pb).

---

## Bioinformática (resumen)

| Paso | Herramienta |
|------|-------------|
| Extracción de códigos de barras | QIIME v1.9.1 |
| Filtrado de calidad, desruidado, eliminación de quimeras | QIIME2 v2023.4 + DADA2 |
| Asignación taxonómica | Scikit-Learn Naive Bayes / GreenGenes2 V3–V4 |
| Eliminación de contaminantes | decontam |
| Análisis de diversidad | R: hillR, vegan, ggplot2, ComplexHeatmap |

Pipeline bioinformático completo: *(agregar liga al repositorio de scripts cuando esté disponible)*

---

## Notas

- La degradación rápida del ADN de plasmodios es un reto conocido (Shchepin et al. 2017); procesar inmediatamente después de la extracción o agregar fenol.
- Ambos métodos detectan los taxa dominantes de forma consistente; difieren en la recuperación de grupos poco abundantes.
- Para el estudio de referencia se usaron plasmodios de 10 días de cultivo en agar avena.

---

## Cita

> Molina-Viramontes JP, Gómez-Acata ES, Hereira-Pacheco S, Estrada-Torres A, Navarro-Noya YE. (2025). Comparison of Methods to Characterize the Microbiota of Myxomycete Plasmodia. *Journal of Eukaryotic Microbiology*, 73, e70058. https://doi.org/10.1111/jeu.70058
