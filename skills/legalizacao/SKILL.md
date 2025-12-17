---
name: legalizacao
description: Specialized workflow for company legalizations (ABERTURA, ALTERACAO, BAIXA) using Trello. Use when user mentions legalizacao, company opening, alteration, closure, or Brazilian company registration processes.
---

# Legalizacao Workflow

Manage company legalization processes in Brazil through Trello integration.

## Overview

This skill handles three types of company legalizations:
- **ABERTURA** - Opening a new company
- **ALTERACAO** - Modifying an existing company
- **BAIXA** - Closing a company

All tasks are created in the dedicated LEGALIZACAO Trello board with automatic checklists and progress tracking.

## Prerequisites

Environment variables must be set:
```bash
export TRELLO_API_KEY="your-api-key"
export TRELLO_TOKEN="your-token"
```

## CLI Commands

The skill provides a CLI tool. Run from the `scripts/` directory:

```bash
# Collect data interactively
node index.js collect ABERTURA

# Create task from collected data
node index.js create ABERTURA

# List saved drafts
node index.js list

# Generate status report
node index.js report

# Show requirements for a type
node index.js requirements ABERTURA

# Clean all drafts
node index.js clean
```

## Workflow Steps

### For ABERTURA (New Company)

1. **Collect required documents:**
   - 3 name options for the company
   - Activities to be performed
   - IPTU of headquarters property
   - Social capital amount
   - Partner documents (RG, CPF)
   - Proof of residence for partners
   - Complete partner qualification
   - Participation percentage in capital

2. **Run data collection:**
   ```bash
   node scripts/index.js collect ABERTURA
   ```

3. **Create Trello task:**
   ```bash
   node scripts/index.js create ABERTURA
   ```

### For ALTERACAO (Company Modification)

Required documents:
- Specific alteration type
- Updated partner documents
- Current company documents
- Social contract

### For BAIXA (Company Closure)

Required documents:
- Reason for closure
- All company documents
- List of pending issues
- Tax clearance certificates

## Board Structure

```
LEGALIZACAO Board
├── RECEBIDAS      (New legalizacoes - entry point)
├── ANALISE        (Under review)
├── EM ANDAMENTO   (In progress)
└── CONCLUIDO      (Completed)
```

All new tasks are created in RECEBIDAS with the ECAB label.

## Task Format

Tasks are created with:
- Title: `[TYPE] - Company Name`
- Category: ECAB
- Priority: Urgente/Importante/Normal
- Due date: As specified
- Checklist: Auto-generated based on type

## Troubleshooting

1. **Missing credentials**: Ensure TRELLO_API_KEY and TRELLO_TOKEN are set
2. **List not found**: Verify access to LEGALIZACAO board and RECEBIDAS list exists
3. **Permission denied**: Check API token has write access

## Data Storage

Draft data is persisted in `~/.legalizacao-data/drafts.json` between sessions.
