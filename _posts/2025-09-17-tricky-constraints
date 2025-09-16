---
title: Constraint builder
description: How to build constraints from datamodels and dataframes
tags:
- Pandas
- Pydantic
- OR-tools
---


# Datamodels and DataFrames to OR-Tools constraints

I have a filtering problem and I just can't see the answer.

I have two data frames, one is for loans, the other is for the assets that secure the loans.

In this specific example we have the cardinality that one loan will have one or many assets
(but in future cases the cardinality may be that one asset may be secured against one or many loans).

Additional information about these dataframe is that they have about $20$ columns, and maybe $100,000$ rows.
The assets DataFrame has a column that references the loan index (like a foreign key).
Both DataFrames have a unique index, so SQL-like joins are totally possible.

For this dataset I'm writing a constraint builder. The constraints arrive in the program as Pydantic datamodels.
The dataset of loans and assets, plus the exact set of constraints are user-defined.
The challenge is that I need an adaptable constraint builder for any set of data and constraints,
this model cannot be hard coded.

I do have a constraint builder for the case of a single dataset, but I'm just struggling
with the extension to the dual dataframe case.

## Proposed solution: (OUTER) JOIN-FILTER-

Although I think the solution here is simply to do:

1. OUTER JOIN on the two dataframes
2. Apply all filters (Some filters apply to asset-based columns, others apply to loan-based columns)
3. Before computing the coefficients,
  - If the coefficients are on asset-based columns, then GROUP-BY loan_id and SUM the coefficients at the loan level
  - Else the coefficients are for loan-based columns, then SELECT UNIQUE loan_id.

Building up the arbitrary list of filters is also challenging.
