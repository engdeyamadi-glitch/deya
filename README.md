# deya
Project files for Deya's HP pipeline homework.
{
  "project": {
    "name": "HP Errors Data Pipeline",
    "description": "End-to-end data architecture model for HP printer error analytics"
  },
  "data_sources": [
    {
      "id": "DS1",
      "name": "Printer Devices",
      "type": "Real Error Producer",
      "format": "JSON"
    },
    {
      "id": "DS2",
      "name": "Testing Simulation System",
      "type": "Synthetic Error Producer",
      "format": "JSON"
    }
  ],
  "data_lake": {
    "id": "DL1",
    "name": "AWS S3 Data Lake",
    "storage_type": "Raw Storage",
    "format": "JSON"
  },
  "data_processing": {
    "id": "P1",
    "name": "Batch Data Processing",
    "operations": [
      "Parsing",
      "Cleaning",
      "Enrichment",
      "Aggregation"
    ],
    "output_format": "Parquet"
  },
  "data_transformation": {
    "id": "T1",
    "name": "Format Transformation",
    "input_format": "Parquet",
    "output_format": "CSV"
  },
  "data_warehouse": {
    "id": "DW1",
    "name": "Relational Analytics Database",
    "db_type": "PostgreSQL",
    "tables": [
      "errors",
      "printers",
      "customers",
      "locations"
    ]
  },
  "query_layer": {
    "views": [
      "critical_errors_last_24_hours",
      "error_rate_per_customer",
      "top_error_codes"
    ]
  },
  "visualization": {
    "tools": [
      "BI Dashboard",
      "Reporting System"
    ],
    "use_cases": [
      "Error trend monitoring",
      "Printer reliability analysis",
      "Customer impact analysis"
    ]
  },
  "data_flow": [
    "Printer Devices -> AWS S3 Data Lake",
    "Simulation System -> AWS S3 Data Lake",
    "AWS S3 Data Lake -> Batch Processing",
    "Batch Processing -> Parquet Storage",
    "Parquet Storage -> Format Transformation",
    "CSV Output -> Data Warehouse",
    "Data Warehouse -> Dashboards"
  ]
}

