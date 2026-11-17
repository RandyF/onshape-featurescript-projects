# Agent Guidelines - Requirements Orientation

## Directory Overview
This directory organizes all project requirements according to the Lightweight Development Process level decomposition hierarchy (L1 through L5).

## Directory Structure & Levels
- `l1_project/`: Level 1 - Project Definition documents (e.g., `pd_000_onshape_featurescript_projects.md`), establishing project scope, budget, objectives, constraints, and roadmaps.
- `l2_architecture/`: Level 2 - System Architecture specifications and high-level architectural component definitions (`architecture_components/`).
- `l3_component/`: Level 3 - Subsystem and Component Requirements defining functional and interface requirements for individual components.
- `l4l5_function_technical_implementation/`: Level 4 & Level 5 - Detailed function contracts, algorithms, and technical implementation specifications.

## Core Rules for Requirements
- **Traceability:** Every requirement at L2-L5 must trace upward to an L1 objective or scope item in PD-000.
- **Groundedness:** Never invent unverified platform features or external services. Mark design assumptions with `[suggested]`.
- **Formatting:** All requirement files must be written in clean GitHub-Flavored Markdown with explicit tables and metadata blocks.
- **Directory Maintenance:** Maintain directory-level `AGENTS.md` files whenever files are added or modified.
