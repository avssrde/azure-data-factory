# Best Practices & Recommendations

### Table Of Contents
- [Naming Convention](#1-naming-convention)
    - [Data Factory](#11-data-factory)
    - [Linked Services / DataSets / Pipelines / DataFlows](#12-linked-services--datasets--pipelines--dataflows)
    - [Integration Runtime](#13-integration-runtime)
    - [Data Flows](#14-data-flows)
    - [Pipeline Parameters & Variables](#15-pipeline-parameters--variables)

### 1. Naming Convention

#### 1.1 Data Factory
- Name must be unique across Microsoft Azure.
- Names are case-insensitive in Microsoft Azure.
- Object name contains only Alphanumeric Character [must be an letter (or) number] and (-) character.
- Object name must start & end with Alphanumeric Character [must be an letter (or) number].
- Consecutive (-) character is not permitted in container names.
- Name Must have character length between [3-63].

#### 1.2 Linked Services / DataSets / Pipelines / DataFlows
- Name must be unique with in Data Factory.
- Names are case-insensitive.
- Object name contains only Alphanumeric Character [must be an letter (or) number] and (_) character.
- Object name must start & end with Alphanumeric Character [must be an letter (or) number].
- The following characters are not allowed: “.”, “+”, “?”, “/”, “<”, ”>”,”*”,”%”,”&”,”:”,”\”
- Dashes ("-") are not allowed in the names of linked services, data flows, & datasets.

#### 1.3 Integration Runtime
- Name must be unique with in Data Factory.
- Names are case-insensitive in Microsoft Azure.
- Object name contains only Alphanumeric Character [must be an letter (or) number] and (-) character.
- Object name must start & end with Alphanumeric Character [must be an letter (or) number].
- Consecutive (-) character is not permitted in container names.

#### 1.4 Data Flows
- Name must be unique with in Data Factory.
- Names are case-insensitive in Microsoft Azure.
- Object name contains only Alphanumeric Character [must be an letter (or) number].
- Object name must start with Alpha Character [must be an letter].

#### 1.5 Pipeline Parameters & Variables
- Name must be unique with in Pipeline scope.
- Always follow your organization naming convention like snake_case, CamelCase, kebab-case.
