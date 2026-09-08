# Education Data Analysis

## Project Overview




---

## Data Structure

The project contains two main groups of information:

### Student and School Information

These datasets describe students, their socioeconomic characteristics, the schools they attend, and their academic results.

- `df_student_info`
- `df_socieconomic_info`
- `df_school_info`
- `df_result_info`

### Teacher Information

These datasets describe different characteristics of teachers and their academic and employment conditions.

- `df_escalafon`
- `df_clei`
- `df_vinculacion`
- `df_asignacion_academica`
- `df_educacion`
- `df_edad`
- `df_jornada`

The different datasets can be related primarily through the **school campus identifier** and the **academic period**.

---

# Student and School Information

## `df_student_info`

This table contains individual-level information about students.

Each row represents a student and contains information about:

- Student identification
- School institution
- School campus
- Demographic characteristics
- Disability status
- Ethnicity
- Gender
- Grade
- Nationality
- Repetition of grade
- Internet and reading habits
- Employment-related characteristics
- Place of residence

The main identifiers are:

```text
student_id
school_institution_id
school_campus_id
```

The original Colombian variable names were renamed to English equivalents:

| Original Variable | New Variable |
|---|---|
| `estu_consecutivo` | `student_id` |
| `cole_cod_dane_establecimiento` | `school_institution_id` |
| `cole_cod_dane_sede` | `school_campus_id` |

---

## `df_socieconomic_info`

This table contains socioeconomic information associated with students and their households.

The variables describe characteristics such as:

- Individual socioeconomic index
- Individual socioeconomic level
- Household size
- Number of siblings
- Number of books
- Parents' education
- Parents' employment
- Housing socioeconomic stratum
- Household economic situation
- Access to internet
- Computer ownership
- Television service
- Washing machine
- Automobile
- Motorcycle
- Video game console
- Household appliances
- Food consumption

The main identifiers are:

```text
student_id
school_institution_id
school_campus_id
```

This table can therefore be connected to `df_student_info` through `student_id`.

---

# `df_school_info`

This table contains information about the educational institution and its campus.

The information includes:

- Geographic location
- School calendar
- School character
- School nature
- Gender configuration
- School schedule
- Institution code
- Campus code
- Institution name
- Campus name
- Main campus status

The campus is identified by:

```text
school_campus_id
```

The dataset is grouped by campus code so that each campus has a single representative value for its characteristics.

For categorical variables, the **mode** is used:

```python
.agg(lambda x: x.mode().iloc[0] if not x.mode().empty else None)
```

This is useful because the original dataset contains multiple student-level observations for the same school campus.

---

# `df_result_info`

This table contains the academic results of students.

The information includes:

- Scores by subject
- Global score
- Percentiles
- Department and municipality where the exam was presented
- Academic period

The main student and school identifiers are:

```text
student_id
school_institution_id
school_campus_id
```

The academic performance variables include:

- Mathematics
- Critical Reading
- Natural Sciences
- Social Sciences and Citizenship
- English
- Global score

This table can be connected to `df_student_info` through `student_id`.

---

# Teacher Information

## `df_escalafon`

This table contains information about teachers according to their **grade or professional classification within the teacher salary/career scale**.

Each row represents a combination of:

```text
SEDE_CODIGO
PERIODO_ID
PERIODO_ANIO
GRADOESCA
```

The table contains information about:

- Campus
- Academic period
- Teacher grade
- Grade code
- Grade name
- Number of male teachers
- Number of female teachers

Example:

```text
SEDE_CODIGO = 308758001975
PERIODO_ANIO = 2015
GRADOESCA_NOMBRE = Grado 7
HOMBRES = 2
MUJERES = 3
```

This allows the analysis of the composition of teachers according to their professional classification.

---

## `df_clei`

This table contains information related to **CLEI (Ciclos Lectivos Integrados)** and other educational models for young people and adults.

Each observation is associated with:

```text
SEDE_CODIGO
PERIODO_ID
PERIODO_ANIO
NIVELENSE
```

The table contains:

- Campus
- Academic period
- Educational level
- Educational level code
- Educational level name
- Number of male individuals
- Number of female individuals

For example:

```text
CLEI
Otros modelos educativos para jóvenes y adultos
```

This dataset allows the analysis of the presence and composition of alternative educational models across campuses and periods.

---

## `df_vinculacion`

This table contains information about the **employment relationship or contractual status of teachers**.

The main categories include:

- Teachers with permanent positions and professional classification
- Contract teachers with professional classification
- Permanent teachers without professional classification
- Other contractual arrangements

The table contains:

```text
SEDE_CODIGO
PERIODO_ID
PERIODO_ANIO
VINCULA_ID
VINCULA_CODIGO
VINCULA_NOMBRE
CANTIDAD_HOMBRES
CANTIDAD_MUJER
```

This dataset can be used to analyze the composition of the teaching workforce according to employment status.

---

## `df_asignacion_academica`

This table contains information about the **academic assignment of teachers**.

It is the largest teacher dataset, containing more than two million observations.

The table describes teacher assignments according to:

- Campus
- Academic period
- Educational level
- Educational specialization
- Academic area
- Number of male teachers
- Number of female teachers

The educational levels include, for example:

```text
Preescolar
Básica primaria
```

Academic areas include:

```text
Matemáticas
Ciencias naturales y educación ambiental
Ciencias sociales
Humanidades
```

among others.

This table provides information about how teachers are distributed across different educational levels and academic areas.

---

## `df_educacion`

This table contains information about the **educational attainment of teachers**.

The available categories include:

- Normalista superior
- Tecnólogo en educación
- Licenciado
- Posgrado en educación o programa pedagógico

The main structure is:

```text
SEDE_CODIGO
PERIODO_ID
PERIODO_ANIO
NIVELEDUCDOC
NIVELEDUCDOC_CODIGO
NIVELEDUCDOC_NOMBRE
```

This dataset can be used to analyze the educational qualifications of teachers across campuses and academic periods.

---

## `df_edad`

This table contains information about the **age range of teachers**.

The age categories include ranges such as:

```text
Entre 26 y 30 años
Entre 36 y 40 años
Entre 46 y 50 años
Entre 51 y 55 años
Mayor a 56 años
```

The main structure is:

```text
SEDE_CODIGO
PERIODO_ID
PERIODO_ANIO
RANGODOCENTE_ID
RANGODOCENTE_NOMBRE
```

This dataset allows the analysis of the age composition of teachers across campuses and periods.

---

## `df_jornada`

This table contains information about the **working schedule or teaching shift of teachers**.

The available information includes:

- Campus
- Academic period
- Year
- Schedule identifier
- Schedule code
- Schedule name
- Number of male teachers
- Number of female teachers

Example:

```text
Jornada = Mañana
Hombres = 2
Mujeres = 0
```

Some earlier observations contain missing values (`NaN`) in the schedule-related fields.

This dataset can therefore be used to analyze the distribution of teachers across different working schedules, while accounting for missing information.

---

# Common Identifiers

A key characteristic of these datasets is the presence of common identifiers.

The most important identifier is:

```text
SEDE_CODIGO
```

which identifies the **school campus**.

The datasets also contain:

```text
PERIODO_ID
PERIODO_ANIO
```

which identify the academic period and year.

Therefore, teacher datasets can generally be interpreted using the combination:

```text
SEDE_CODIGO + PERIODO_ANIO
```

This combination represents a particular school campus during a specific academic year.

---

# Relationship Between Datasets

The overall conceptual structure can be represented as:

```text
                         SCHOOL CAMPUS
                       school_campus_id
                              │
               ┌──────────────┴──────────────┐
               │                             │
        STUDENT INFORMATION           TEACHER INFORMATION
               │                             │
       ┌───────┼────────┐          ┌─────────┼─────────────┐
       │       │        │          │         │             │
   Student  Socio-   Results    Education   Age       Employment
    Info   economic             │           │        /Vinculación
                                 │           │
                              Jornada   Escalafón
                                 │
                         Academic Assignment
                                 │
                                CLEI
```

The central concept is the **school campus**, which allows student and teacher information to be connected.

At the student level:

```text
school_campus_id
       │
       ├── df_student_info
       ├── df_socieconomic_info
       └── df_result_info
```

At the teacher level:

```text
school_campus_id + period
       │
       ├── df_escalafon
       ├── df_clei
       ├── df_vinculacion
       ├── df_asignacion_academica
       ├── df_educacion
       ├── df_edad
       └── df_jornada
```

---

# Temporal Structure

The datasets cover multiple academic periods.

For example, the teacher datasets shown contain observations from:

```text
2015
...
2024
```

This temporal structure makes it possible to perform longitudinal analyses.

For example:

- Changes in teacher qualifications over time
- Changes in teacher age composition
- Changes in employment relationships
- Changes in academic assignments
- Changes in educational models
- Changes in school composition
- Relationships between teacher characteristics and student performance

---

# Data Transformation

The original datasets use Spanish variable names and categorical values.

As part of the data preparation process, variables can be renamed into English to create a consistent analytical schema.

For example:

```text
SEDE_CODIGO
        ↓
school_campus_id

ESTU_CONSECUTIVO
        ↓
student_id

COLE_COD_DANE_ESTABLECIMIENTO
        ↓
school_institution_id
```

This creates a common naming convention across the different datasets.

---

# Analytical Objective




---

# Dataset Summary



---

## Data Characteristics

The datasets differ considerably in size.

For example:

```text
df_escalafon              ≈ 133,496 rows
df_clei                    ≈ 21,493 rows
df_vinculacion             ≈ 629,998 rows
df_asignacion_academica    ≈ 2,313,572 rows
df_educacion               ≈ 2,040,116 rows
df_edad                    ≈ 2,040,116 rows
df_jornada                 ≈ 2,040,116 rows
```

This difference in size reflects the different levels of aggregation and granularity of each source.

In particular, `df_asignacion_academica` contains multiple records for the same campus and period because a campus can have multiple educational levels, specialties, and academic areas.

---

## Language

The original datasets were produced in **Spanish**, corresponding to the official language used in Colombia.

The analytical database uses English variable names to provide a consistent naming convention and facilitate integration with Python, SQL, and other analytical tools.