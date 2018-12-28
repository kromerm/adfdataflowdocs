# ADF Data Flow for SSIS Developers

| SSIS                 | ADF              |
|----------------------|------------------|
| Destination          | Sink             |
| Toolbox              | Plus Sign        |
| Multicast            | New Branch       |
| Data Flow DTS Engine | Azure Databricks |
| Connection Manager   | Connections      |
| SSDT                 | UI               |
| Connections          | Linked Service   |
| Joins (Merge Join)   | Join (Hash or replicated / broadcast join)  |
| Column Selectivity   | As opposed to dropping columns in transformation steps, ADF Data Flow passes all columns through the entire Data Flow. This way, we can better handle schema drift conditions. To remove columns from your flow, use the Select transform |
| Auto-create destination table | Sink Transformation SQL DB & SQL DW option in Dataset. Use the "Edit" checkbox and enter the name of the new destination table to be auto-created. |


