# Dig-One

Privacy-first Excel automation platform with local processing, deterministic rules, AI planning and enterprise-grade auditability.

## Intelligence OS — Base de Renseignement

Dig-One intègre une couche d'intelligence fondée sur la collecte, classification, provenance, intégrité, preuve, corroboration, contradiction, vérification et analyse de renseignements issus de sources légalement accessibles.

**Principe directeur :**

`INFORMATION → PREUVE → VÉRIFICATION → ANALYSE → RISQUE → DÉCISION`

## Pipeline opérationnel

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

## Règle fondamentale

`HYPOTHESIS` est totalement exclu du modèle opérationnel.

Il n'existe aucune transition `HYPOTHESIS → FACT`.

Le raisonnement du LLM n'est jamais une preuve. La confiance du LLM n'est jamais une vérification. La sortie du LLM n'est jamais une source.

```text
SOURCE ≠ CONTENT ≠ ASSERTION ≠ EVIDENCE ≠ VERIFICATION ≠ FACT ≠ ANALYSIS
```

## Classification primaire

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

## Statuts autorisés

- RAW
- OBSERVED
- CORROBORATED
- VERIFIED
- INSUFFICIENT
- CONTESTED
- REJECTED
- DERIVED

`HYPOTHESIS` et tout statut équivalent sont exclus.

## Content Model

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

## Data Contract — INTELLIGENCE_OBJECT v1.0

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

### Verified Fact

Un fait vérifié n'est jamais un simple `is_fact: true`.

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

## Classification Engine

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

Le moteur sépare :

- **WHAT IS IT?** → TYPE
- **WHAT DOES IT SAY?** → CONTENT
- **WHERE DID IT COME FROM?** → PROVENANCE
- **WHAT CAN WE ESTABLISH?** → VERIFICATION STATUS

## Integrity Gate

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

Résultats : `PASS`, `FAIL`, `REQUIRES_REVIEW`.

Pour `VERIFIED`, une preuve et un enregistrement de vérification doivent exister. Toute transition de statut et toute référence importante doivent rester traçables.

## Rôle du LLM

Le LLM peut classifier, extraire, normaliser, détecter des entités, identifier des assertions, comparer des contenus, rechercher des contradictions et produire une analyse explicitement dérivée des éléments documentés.

Il ne remplace ni la source, ni la preuve, ni la provenance, ni la vérification, ni l'audit.

## Roadmap

1. Content Taxonomy
2. Data Contract
3. Source Model
4. Evidence Model
5. Claim Model
6. Entity Model
7. Verification Model
8. Traceability Model
9. Classification Engine
10. Intelligence / Monitoring

## Documentation

La spécification complète est disponible dans [`docs/INTELLIGENCE_OS_PROTOCOL.md`](docs/INTELLIGENCE_OS_PROTOCOL.md).

## État

**Étape 2 — Data Contract v1.0 en construction.**
