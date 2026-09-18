## From language to pain: brain-behavior representations of hypnotic verbal suggestions

Analysis code for the study:

From language to pain: brain-behavior representations of hypnotic verbal suggestions for pain modulation

This project investigates how verbal suggestions are encoded in the brain and how these representations are subsequently expressed during pain modulation. Using fMRI data from a standardized hypnotic suggestion paradigm, we examine inter-subject convergence during suggestion encoding and pain processing, and relate these neural representations to individual differences in hypnotic suggestibility and behavioral pain modulation.

The study included 23 participants and used an inter-subject similarity framework across 216 brain regions (200 cortical parcels from the Schaefer atlas + 16 subcortical regions).

**Preprint**

The manuscript is available as a bioRxiv preprint:

From language to pain: brain-behavior representations of hypnotic verbal suggestions for pain modulation

bioRxiv: 10.64898/2026.07.22.740147

Analysis overview

The analyses follow a progression from behavioral effects, to temporal inter-subejct correlations during suggestion encoding, to spatial inter-subject pattern similarity during pain processing, and finally to relationships between these stages.

Most scripts are meant to be ran from the commad line, but are also built for to tun interactively like a Jupyter notebook.


**Behavioral stats and visualization**

`visualization_behavioral.py`

**Inter-subject correlation (ISC)**

ISC quantifies the similarity of BOLD time series between pairs of participants while they listen to the same verbal suggestions.

ISC was computed independently for each of the 216 brain regions and for the four experimental conditions:

One-sample tests of ISC against zero
Comparisons between conditions
Visualization of ISC maps and pairwise similarity matrices projected onto the brain atlas

`main_isc.py` : Main ISC analysis
`visualization_isc.py` : ISC visualization and final plots

3. Inter-subject representational similarity analysis (IS-RSA)

IS-RSA tests whether similarity between participants in one domain predicts similarity in another domain.

The primary behavioral model is the Anna Karenina (AnnaK) model based on SHSS. The model tests whether participants with similar levels of hypnotic suggestibility show similar neural responses.

Two behavioral similarity models are used:

AnnaK similarity (Finn et al., 2020)
Euclidean similarity : similarity between participants irrespective of their position along the suggestibility continuum

Neural similarity is evaluated using:

Pearson-based ISC during suggestion encoding
Dot-product-based IS-MVPS during pain processing

Spearman correlations between behavioral and neural similarity matrices are evaluated using non-parametric permutation testing.

Main script: `isc-RSA_ext_conds_sugg-pain_tian216_2tails.py`

Visualization: `visu_rsa_isc_ext_model.py`

4. Inter-subject multivoxel pattern similarity (IS-MVPS)

Pain processing

Pain-related spatial representations are obtained from first-level GLM contrast maps:

Hypoalgesia > NeutralHYPO
Hyperalgesia > NeutralHYPER

For each of the 216 regions, multivoxel patterns are extracted and compared between participants.

The final similarity metric is the dot product, which captures both the direction and magnitude of spatial activation patterns. These pairwise similarity matrices are then used for IS-RSA.

Main script: `rsa_mvpa_from_glm_pain_variables.py`

5. Cross-region IS-RSA

The cross-region analysis tests whether similarity during suggestion encoding is related to similarity during pain modulation.

Specifically:

ISC during suggestion encoding → IS-MVPS during pain

A region showing similar temporal dynamics across two participants during suggestion encoding is tested for its relationship with the similarity of their spatial pain-modulation patterns in another region.

Seed regions are defined from the suggestion-encoding IS-RSA results, and target regions from the pain-related IS-RSA results.

Main script: `rsa_isc_mvpa.py`

This analysis provides the link between the neural representation of verbal suggestions and their subsequent implementation during pain.

6. IS-RSA with behavioral pain modulation

The IS-RSA framework is additionally extended from hypnotic suggestibility to behavioral changes in pain ratings.

An AnnaK similarity model is constructed from:

Hypoalgesia − NeutralHYPO
Hyperalgesia − NeutralHYPER

This tests whether participants with similar behavioral pain modulation also show similar multivoxel pain-related representations.

A key analysis examines the relationship between PHG pattern similarity and behavioral hypoalgesia.

Main script: `rsa_mvpa_from_glm_pain_variables.py`

Visualization: `visualization_is-rsa_final.py`

### Software

The analyses were implemented in Python 3.11.

Main neuroimaging packages include:

BrainIAK
Nilearn

### Repository structure


├── scripts/           # Main analysis scripts
├── src/               # source code for scripts () 
├── visualization/     # Visualization and publication figures
├── ...
└── README.md

### Data availability

The individual-level fMRI data are not publicly shared because the original consent did not authorize sharing of individual data outside the research group. The repository therefore contains the analysis code but not the underlying participant data or derived output datasets.

### Citation

If you use this code or build upon these analyses, please cite:

Sutterlin-Guindon, D., Picard, M.-E., Chen, J.-I., Landry, M., Brambati, S., Ogez, D., Piché, M., & Rainville, P.
From language to pain: brain-behavior representations of hypnotic verbal suggestions for pain modulation.
bioRxiv, 2026.

### Contact

Dylan Sutterlin-Guindon : dylan.sutterlin-guindon@umontreal.ca
Université de Montréal / CRIUGM


