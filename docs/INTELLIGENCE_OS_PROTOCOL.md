# Intelligence OS — Base de Renseignement

## 0. Mission

Dig-One peut intégrer un moteur d'intelligence fondé sur la collecte, la classification, la provenance, l'intégrité, la preuve, la corroboration, la contradiction, la vérification et l'analyse de renseignements issus de sources légalement accessibles.

Principe directeur :

`INFORMATION → PREUVE → VÉRIFICATION → ANALYSE → RISQUE → DÉCISION`

Le système reste dans un périmètre légal et traçable. Il ne constitue pas un service clandestin et ne doit pas être utilisé pour l'interception non autorisée, la surveillance illégale ou l'accès non autorisé à des systèmes.

## 1. Pipeline opérationnel

```text
INPUT
→ INGESTION
→ IDENTIFICATION
→ CLASSIFICATION
→ EXTRACTION
→ PROVENANCE
→ INTEGRITY
→ OBSERVATION
→ EVIDENCE
→ CORROBORATION
→ CONTRADICTION
→ VERIFICATION
→ ANALYSIS
→ INTELLIGENCE PRODUCT
→ MONITORING
```

Aucune étape n'est implicitement considérée comme terminée.

## 2. Règle fondamentale : HYPOTHESIS exclu

`HYPOTHESIS` est totalement exclu du modèle opérationnel.

Il n'existe aucune transition :

```text
HYPOTHESIS → FACT
```

Le raisonnement du LLM n'est jamais une preuve.
La confiance du LLM n'est jamais une vérification.
La sortie du LLM n'est jamais une source.

Une information, une assertion ou une analyse ne devient un fait vérifié que par l'existence d'une preuve traçable et d'un enregistrement de vérification conforme au modèle.

## 3. Séparation des objets

```text
SOURCE
≠ CONTENT
≠ ASSERTION
≠ EVIDENCE
≠ VERIFICATION
≠ FACT
≠ ANALYSIS
```

### Source
Origine identifiable d'une information.

### Content
Contenu effectivement observé dans la source.

### Assertion
Proposition exprimée ou extraite du contenu.

### Evidence
Élément traçable permettant de soutenir ou réfuter une assertion.

### Verification
Procédure et résultat permettant d'établir le statut d'une assertion.

### Verified Fact
Assertion ayant satisfait les exigences de preuve et de vérification.

### Analysis
Interprétation analytique construite à partir d'objets déjà documentés. L'analyse ne modifie pas le statut probatoire des sources.

## 4. Taxonomie primaire

- DOCUMENT
- WEB
- COMMUNICATION
- STRUCTURED_DATA
- MULTIMEDIA
- TECHNICAL
- EVENT
- RECORD
- METADATA
- UNKNOWN

## 5. Sous-types

### DOCUMENT
- PDF
- DOCX
- XLSX
- CSV
- REPORT
- CONTRACT
- REGISTRY
- FINANCIAL
- LEGAL
- ADMINISTRATIVE

### WEB
- NEWS
- COMPANY_PAGE
- GOVERNMENT
- REGISTRY
- DATABASE
- BLOG
- FORUM
- SOCIAL
- MARKETPLACE
- DOCUMENTATION

### COMMUNICATION
- EMAIL
- MESSAGE
- PRESS_RELEASE
- INTERVIEW
- STATEMENT
- TRANSCRIPT

### STRUCTURED_DATA
- JSON
- XML
- CSV
- TABLE
- API_RESPONSE
- DATABASE_RECORD

### MULTIMEDIA
- IMAGE
- SCAN
- SCREENSHOT
- VIDEO
- AUDIO
- OCR
- TRANSCRIPTION

### TECHNICAL
- LOG
- CODE
- CONFIG
- DOMAIN
- IP
- CERTIFICATE
- HASH
- IOC
- VULNERABILITY

### EVENT
- CREATION
- MODIFICATION
- ACQUISITION
- APPOINTMENT
- ANNOUNCEMENT
- LEGAL_EVENT
- SANCTION
- INCIDENT
- STATUS_CHANGE

## 6. Dimensions sémantiques

- FACTUAL_OBSERVATION
- ASSERTION
- QUOTE
- OPINION
- ANALYSIS
- EVENT
- ENTITY
- RELATIONSHIP
- NUMBER
- DATE
- LOCATION
- METADATA

## 7. Décomposition du contenu

```text
CONTENT
├── ENTITIES
│   ├── PERSON
│   ├── COMPANY
│   ├── ORGANIZATION
│   ├── LOCATION
│   ├── DOMAIN
│   └── OTHER
├── TEMPORAL
│   ├── DATE
│   ├── PERIOD
│   └── TIMESTAMP
├── EVENTS
├── RELATIONSHIPS
├── NUMERIC DATA
├── ASSERTIONS
├── QUOTES
└── METADATA
```

## 8. Provenance

Types de provenance :

- PRIMARY_SOURCE
- SECONDARY_SOURCE
- TERTIARY_SOURCE
- USER_PROVIDED
- SYSTEM_GENERATED
- DERIVED
- UNKNOWN

La provenance doit être conservée avec l'objet et ne peut être remplacée par une inférence du LLM.

## 9. Statuts opérationnels autorisés

```text
RAW
OBSERVED
CORROBORATED
VERIFIED
INSUFFICIENT
CONTESTED
REJECTED
DERIVED
```

`HYPOTHESIS` et tout statut équivalent ne sont pas valides.

`INSUFFICIENT` est utilisé lorsque les éléments disponibles ne permettent pas d'établir le statut requis.

`CONTESTED` est utilisé lorsqu'une contradiction documentée existe.

`REJECTED` est utilisé lorsqu'une assertion ou un objet a été invalidé selon une procédure traçable.

`DERIVED` désigne une information calculée ou construite à partir d'objets sources ; elle n'est pas automatiquement un fait vérifié.

## 10. Data Contract — INTELLIGENCE_OBJECT v1.0

Chaque objet doit contenir les domaines suivants :

```text
identity
classification
provenance
temporal
content
entities
assertions
evidence
relationships
verification
integrity
audit
```

### Identity

```text
object_id
object_type
version
created_at
updated_at
```

### Classification

```text
primary_type
subtype
source_type
semantic_types[]
content_format
```

### Provenance

```text
source_id
source_type
origin
author
collection_method
collected_at
published_at
```

### Content

```text
raw_reference
normalized_content
language
content_hash
```

## 11. Verified Fact Contract

Un fait vérifié ne doit jamais être représenté par un simple booléen tel que `is_fact: true`.

Structure minimale :

```text
VERIFIED_FACT
├── fact_id
├── claim_id
├── evidence_refs[]
├── source_refs[]
├── verification_id
├── verified_at
├── verifier
└── audit_record
```

## 12. Classification Engine

Le moteur répond séparément à quatre questions :

```text
WHAT IS IT?      → TYPE
WHAT DOES IT SAY? → CONTENT
WHERE DID IT COME FROM? → PROVENANCE
WHAT CAN WE ESTABLISH? → VERIFICATION STATUS
```

Pipeline :

```text
CONTENT INPUT
→ FORMAT DETECTION
→ CONTENT TYPE
→ SUBTYPE
→ SOURCE TYPE
→ SEMANTIC ELEMENTS
→ ENTITY EXTRACTION
→ ASSERTION EXTRACTION
→ TEMPORAL EXTRACTION
→ EVIDENCE IDENTIFICATION
→ CLASSIFICATION RECORD
```

## 13. Vérification et corroboration

Une assertion importante doit pouvoir être reliée à :

```text
ASSERTION
→ EVIDENCE
→ SOURCE
→ PROVENANCE
→ VERIFICATION
→ AUDIT RECORD
```

La corroboration augmente la robustesse lorsqu'elle provient de sources indépendantes ou de natures différentes. La simple répétition d'une même information par plusieurs sources dérivées ne constitue pas automatiquement une corroboration indépendante.

Toute contradiction pertinente doit être recherchée et enregistrée avant une conclusion de vérification.

## 14. Integrity Gate

Chaque objet doit passer :

```text
SCHEMA CHECK
→ TYPE CHECK
→ PROVENANCE CHECK
→ REFERENCE CHECK
→ INTEGRITY CHECK
→ STATUS CHECK
→ TRANSITION CHECK
→ AUDIT RESULT
```

Résultats :

- PASS
- FAIL
- REQUIRES_REVIEW

Règles minimales :

- Rejeter un objet si les champs obligatoires d'identité, classification, provenance, preuve ou vérification sont absents lorsque requis.
- Pour `VERIFIED`, une preuve et un enregistrement de vérification doivent exister.
- Toute référence doit être résoluble et traçable.
- Toute transition de statut doit être enregistrée.
- Toute modification substantielle doit préserver l'historique nécessaire à l'audit.

## 15. Modèle de décision

```text
COLLECT
→ IDENTIFY
→ CLASSIFY
→ EXTRACT
→ PRESERVE
→ CORROBORATE
→ CONTRADICT
→ VERIFY
→ ANALYZE
→ PRODUCE
→ MONITOR
```

L'analyse intervient après la vérification des éléments factuels pertinents. Une conclusion analytique doit référencer les objets qui la soutiennent.

## 16. Architecture logique cible

```text
                    ┌─────────────────────┐
                    │       INPUT         │
                    └──────────┬──────────┘
                               ↓
                    ┌─────────────────────┐
                    │     INGESTION       │
                    └──────────┬──────────┘
                               ↓
             ┌────────────────────────────────┐
             │ IDENTIFICATION / CLASSIFICATION│
             └───────────────┬────────────────┘
                             ↓
             ┌────────────────────────────────┐
             │ EXTRACTION / PROVENANCE        │
             └───────────────┬────────────────┘
                             ↓
             ┌────────────────────────────────┐
             │ INTEGRITY / OBSERVATION        │
             └───────────────┬────────────────┘
                             ↓
             ┌────────────────────────────────┐
             │ EVIDENCE / CORROBORATION       │
             └───────────────┬────────────────┘
                             ↓
             ┌────────────────────────────────┐
             │ CONTRADICTION / VERIFICATION   │
             └───────────────┬────────────────┘
                             ↓
             ┌────────────────────────────────┐
             │ ANALYSIS / INTELLIGENCE PRODUCT│
             └───────────────┬────────────────┘
                             ↓
                    ┌─────────────────────┐
                    │     MONITORING      │
                    └─────────────────────┘
```

## 17. Rôle du LLM

Le LLM peut :

- classifier ;
- extraire ;
- normaliser ;
- détecter des entités ;
- identifier des assertions ;
- proposer des relations ;
- comparer des contenus ;
- rechercher des contradictions ;
- produire une analyse explicitement dérivée des éléments vérifiés.

Le LLM ne peut pas, par sa seule sortie :

- créer une source ;
- créer une preuve ;
- transformer une assertion en fait vérifié ;
- certifier l'authenticité d'un document sans mécanisme de vérification approprié ;
- remplacer la provenance ;
- remplacer l'audit.

## 18. Auditabilité

Chaque décision importante doit permettre de reconstruire :

```text
WHO
WHAT
WHEN
FROM WHERE
USING WHICH EVIDENCE
UNDER WHICH VERIFICATION
WITH WHICH TRANSITION
RESULTING IN WHICH OUTPUT
```

L'objectif est une chaîne de traçabilité reproductible et inspectable.

## 19. Roadmap contrôlée

1. Content Taxonomy — définition et verrouillage
2. Data Contract v1.0 — formalisation
3. Source Model v1.0 — identité, provenance, historique
4. Evidence Model v1.0 — définition et références
5. Claim Model v1.0 — assertions et statut
6. Entity Model v1.0 — personnes, organisations, sociétés, lieux, domaines
7. Verification Model v1.0 — règles et résultats
8. Traceability Model v1.0 — chaîne d'audit
9. Classification Engine — implémentation
10. Intelligence / Monitoring — produits et surveillance légitime

## 20. Gate de progression

Une étape ne passe à l'étape suivante que lorsque son contrat, ses invariants et ses tests sont suffisamment définis pour empêcher une ambiguïté critique.

Aucune autonomie d'agent ne doit contourner les contrats de données, les contrôles d'intégrité, la provenance ou les règles de vérification.

## 21. État initial

Le modèle Intelligence OS est intégré à Dig-One comme spécification documentaire.

État de construction : **Étape 2 — Data Contract v1.0 en construction.**

Le code applicatif doit être ajouté progressivement après verrouillage des contrats, des invariants et des tests.
