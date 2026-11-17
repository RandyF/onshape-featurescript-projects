| Field | Value |
| :--- | :--- |
| **Document ID** | PD-002 |
| **Document Title** | Project Definition: Flat Surface Drawing Mode |
| **Document Type** | Level 1: Sub-Project Definition (PD) |
| **Parent Project** | OnShape FeatureScript Projects Library (PD-000) |
| **Sub-Project** | Flat Surface Drawing Mode (LOGO Turtle Engine dependency) |
| **Version** | 1.0 |
| **Date** | 2026-11-16 |
| **Status** | Draft / Baseline |

---

## 1. Project Overview

### 1.1 Purpose

The Flat Surface Drawing Mode is a sub-project that extends the LOGO Turtle Engine to interpret and process flat surface drawing commands (e.g., PENCIRCLE, PENUP, PENDOWN) within the OnShape FeatureScript environment. It enables the turtle to navigate along predefined 2D geometric shapes on planar surfaces and generate corresponding line segment paths for further modeling operations.

### 1.2 Project Objectives

- Implement LOGO graphics primitives compatible with OnShape FeatureScript: PENCIRCLE, PENUP, PENDOWN
- Process flat surface drawing commands from a 2D shape input
- Navigate the turtle along boundary or interior paths of planar geometry
- Generate composite line segment paths representing drawn shapes
- Provide configuration for surface orientation and plane alignment

### 1.3 Target Environment

- **Platform:** OnShape Online Platform (Cloud CAD)
- **Language / Runtime:** OnShape FeatureScript Environment (server-side runtime)
- **Integration:** EXTends LOGO Turtle Engine (PD-001); consumes path recording functionality
- **Dependency:** LOGO Turtle Engine (PD-001) must be complete and functional before this sub-project can be developed

### 1.4 Primary Deliverables

| Deliverable | Description | Priority |
| :--- | :--- | :--- |
| Flat Surface Drawing Core Module | Centralized module processing drawing commands on planar surfaces | High |
| PENCIRCLE Implementation | Draw circles with configurable radius and center point on flat surface | High |
| PENUP/PENDOWN Implementation | Control turtle "pen state" for continuous/continuous line rendering | Medium |
| 2D Shape Path Generator | Translate 2D polygon/circle paths into 3D line segments | High |

### 1.5 Project Constraints

#### 1.5.1 Technical Constraints

- **OnShape FeatureScript Environment:** All operations must execute within OnShape's server-side runtime
- **Flat Surface Assumption:** Turtle movement is constrained to a single planar surface (plane equation defined)
- **2D-to-3D Projection:** Flat shapes are projected onto the 3D OnShape workspace using plane alignment
- **Surface Orientation:** Plane normal vector must be configurable for arbitrary flat surface orientations

#### 1.5.2 Operational Constraints

- **Input Format:** Accepts 2D geometric primitives (circles, polygons) in planar coordinate space
- **Output Format:** Generates 3D line segment path that replicates the projected drawing commands
- **Default Surface:** Plane aligned with XY-plane (Z=0) unless explicitly configured
### 1.6 Out-of-Scope Requirements

As this initial sub-project:

- Path Following Modes are out of scope (reserved for PD-003; boundary navigation is a separate capability)
- Supports only planar flat surfaces; curved/rotated surface support is deferred
- No hardware integration or physical machine interaction required
- Not production-ready for commercial manufacturing workflows

---

## 2. Project Scope

### 2.1 In-Scope Requirements

The Flat Surface Drawing Mode sub-project defines the boundary between basic LOGO navigation (PD-001) and advanced path following capabilities:

**Core Drawing Functions:**

- **PENCIRCLE Command Implementation:** Draw a circle on the flat surface with configurable radius from center point
- **PENUP Command Implementation:** Lift turtle pen from surface before next drawing command
- **PENDOWN Command Implementation:** Place turtle pen on surface to continue drawing mode
- **2D-to-3D Projection:** Project planar 2D shapes onto 3D OnShape workspace using plane alignment
- **Surface Plane Configuration:** Allow arbitrary flat surface orientation via normal vector or plane equation input

**Boundary Rotation Constraints:**

- Drawing operations are constrained to a single planar surface
- Surface rotation is configurable but subsequent drawing commands remain within that surface plane
- No out-of-plane movement allowed (turtle stays on defined plane during drawing)
- Path following will only occur after completion of the flat surface drawing phase

### 2.2 Out-of-Scope Requirements

As this initial sub-project:

- Path Following Modes are out of scope (reserved for PD-003; boundary navigation is a separate capability)
- Arbitrary LOGO graphics primitives beyond PENCIRCLE, PENUP, PENDOWN are not in scope
- Hardware integration or automation systems are excluded
- Physical manufacturing and CAM implementation deferred to commercial product development
