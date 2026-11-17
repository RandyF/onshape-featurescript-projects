# Agent Guidelines - Workspace Orientation: OnShape FeatureScript Projects

## Workspace Overview
This directory contains an open-ended development library for FeatureScript projects in OnShape. Your job is to help maintain the library code, utilities, and requirements across all sub-projects. Follow guidelines to create documentation and requirements using the Lightweight Development Process as needed.

## Core Rules & Invariants
- **All Requirements Follow Lightweight Process:** All requirements follow the Lightweight Development Process available in global context.
- **Grounded Content:** Avoid assumptions, unverified claims, or undocumented external services. Couch necessary design assumptions with `[suggested]`.
- **Directory Maintenance:** Keep directory-level `AGENTS.md` files updated whenever adding, renaming, or re-scoping files.
- **Code Output:** All code in this project shall be OnShape FeatureScript (`.fs`).

## Architecture Map & Context Index
- `README.md` -> Workspace summary and onboarding.
- `requirements/AGENTS.md` -> Requirements structure index and multi-level guidelines.
  - Level 1: `requirements/l1_project/pd_000_onshape_featurescript_projects.md` -> Master Project Definition for OnShape FeatureScript Projects Library.
  - Level 2: `requirements/l2_architecture/AGENTS.md` -> System Architecture & Component boundaries.
  - Level 3: `requirements/l3_component/AGENTS.md` -> Component specifications.
  - Level 4/5: `requirements/l4l5_function_technical_implementation/AGENTS.md` -> Function specs & technical implementation contracts.
