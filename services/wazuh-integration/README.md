# Wazuh Integration Service

AI-powered webhook receiver for Wazuh alerts with intelligent triage and enrichment.

## Overview

This service bridges Wazuh SIEM with AI-powered alert analysis:

1. **Receives** Wazuh alerts via webhook (POST /webhook)
2. **Transforms** alerts to standardized format
3. **Analyzes** with Alert Triage LLM service
4. **Enriches** high-severity alerts (>= 8) with RAG context
5. **Returns** structured analysis with recommendations

## Architecture

```
Wazuh Manager -> Integration Service -> Alert Triage LLM
                      |
                      | (if severity >= 8)
                      V
                   RAG Service (MITRE enrichment)
```

## Configuration

Environment variables (loaded from .env):

| Variable | Default | Description |
|----------|---------|-------------|
| `WAZUH_MANAGER_URL` | `http://wazuh-manager:55000` | Wazuh API endpoint |
| `API_USERNAME` | `wazuh-wui` | Wazuh API username |
| `API_PASSWORD` | - | Wazuh API password (required) |
| `MIN_SEVERITY` | `7` | Minimum rule level to process |
| `RAG_SEVERITY_THRESHOLD` | `8` | Trigger RAG enrichment threshold |
| `ALERT_TRIAGE_URL` | `http://alert-triage:8000`