# Backstage Templates

This directory contains Backstage Software Templates for scaffolding new components and services.

## Available Templates

### Register New Component

**Location**: `register-new-component/`
**Purpose**: Register existing software components in the Backstage catalog

Features:

- Component metadata collection (name, description, type, lifecycle, owner)
- GitHub repository selection from existing repositories
- Optional integrations:
  - ArgoCD applications
  - CircleCI projects
  - PagerDuty services
  - Sentry projects
  - TechDocs configuration
- Creates a PR with `catalog-info.yaml` and optional TechDocs structure

### Update Existing Component

**Location**: `update-existing-component/`
**Purpose**: Update catalog entries for existing components

## Usage

1. Start Backstage: `yarn dev`
2. Navigate to "Create" in the sidebar
3. Select a template and fill out the form
4. The template will create a PR in your repository with the necessary files

## Template Structure

Templates follow the [Backstage Software Template format](https://backstage.io/docs/features/software-templates/writing-templates):

- `template.yaml` - Template definition with parameters and steps
- `skeleton/` - Template files that get processed and copied
- `README.md` - Template documentation
