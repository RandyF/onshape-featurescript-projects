# PD-000: OnShape FeatureScript Projects Library

| Field | Value |
| :--- | :--- |
| **Document ID** | PD-000 |
| **Document Title** | Project Definition: OnShape FeatureScript Projects Library |
| **Document Type** | Level 1: Project Definition (PD) |
| **Project** | OnShape FeatureScript Projects Library |
| **Version** | 1.1 |
| **Date** | 2026-11-16 |
| **Status** | Approved / Baseline |

---

## 1. Project Overview

### 1.1 Purpose
This project is an open-ended initiative establishing a shared development library and codebase for FeatureScript work within the OnShape platform. The primary objective is to build and maintain a modular repository of reusable algorithms, geometric helpers, utilities, and procedural modeling patterns to support multiple independent FeatureScript sub-projects over time.

### 1.2 Project Objectives
- Establish an open-ended, modular library for OnShape FeatureScript development.
- Provide a reusable foundation of geometry utilities, mathematical routines, and CAD feature patterns.
- Define consistent architectural conventions, metric unit standards, and documentation practices across all sub-projects.
- Serve as the parent project container where individual sub-projects are housed, developed, and maintained over time.

### 1.3 Target Environment
- **Platform:** OnShape Online Platform (Cloud CAD)
- **Language / Runtime:** OnShape FeatureScript Environment (server-side runtime executing OnShape's domain-specific language with JavaScript/C++-style syntax)

---

## 2. Project Scope

### 2.1 In-Scope Requirements
Development of a shared FeatureScript library for the OnShape Online Platform:

- **Open-Ended Development Library:**
  - Modular library structure for reusable FeatureScript routines, types, and helper functions.
  - Scalable repository architecture accommodating diverse sub-projects over time.
- **Dimensional Standards & Units:**
  - All measurements defined in metric units (`mm`, `cm`, `m`, `rad`, `deg`).
  - Standard SI unit prefix support via native FeatureScript `ValueWithUnits`.
  - Independent of specific hardware or machining tool constraints.
- **Process & Documentation Consistency:**
  - Adoption of the Lightweight Development Process for all child requirements and sub-projects.

### 2.2 Out-of-Scope Requirements
- Monolithic deliverables or fixed features belonging to individual sub-projects (sub-projects define their own scope).
- Hardware integration or automation systems.
- Physical manufacturing and CAM implementation.
- Production-ready external deployment workflows / CI/CD pipelines.
- Specific hardware calibration or physical machine tuning.
- Commercial product development.
- Offline FeatureScript execution (OnShape is strictly cloud-native).

---

## 3. Budget and Resource Allocation

### 3.1 Project Budget
- **Total Project Budget:** \$0.00 USD
- **Nature of Project:** Open-ended hobby / personal development library with zero budget allocation. All work is conducted using free OnShape platform resources and self-developed code.

| Category | Budget Allocated | Notes |
| :--- | :--- | :--- |
| **Development** | \$0.00 | Open-ended hobby library |
| **Materials / Components** | \$0.00 | No physical hardware required |
| **Testing & Validation** | \$0.00 | In-CAD verification per sub-project |
| **Software Licenses** | \$0.00 | Standard OnShape account access (free tier) |
| **Professional Services** | \$0.00 | Self-developed code |

### 3.2 Resource Requirements
- **Account / Software:** Standard OnShape account with FeatureScript editor and custom feature capabilities `[suggested]`.
- **Development Time:** Unspecified (open-ended project cadence).
- **External Dependencies:** None (no external hardware, npm packages, or third-party web services).

---

## 4. Project Roadmap

*No fixed roadmap.*

As an open-ended library project, there is no predetermined delivery schedule, milestone dates, or fixed release timeline. Sub-projects, library modules, and utilities are developed and integrated iteratively over time as new requirements and exploration interests arise.

---

## 5. Technical Specifications

### 5.1 FeatureScript Language and Environment

| Attribute | Specification |
| :--- | :--- |
| **Runtime** | OnShape Cloud FeatureScript Engine |
| **Execution Mode** | Server-side execution during CAD regeneration cycles |
| **Language Baseline** | FeatureScript (strictly-typed, domain-specific CAD programming language) |
| **Dependencies** | Standard OnShape FeatureScript library (`geometry.fs`, `sketch.fs`, `units.fs`); no external dependencies |

### 5.2 Parameter Types
All parameters and library interfaces are defined using standard FeatureScript types and metric unit conventions:

| Parameter Type | Description | Usage Example |
| :--- | :--- | :--- |
| **Length / ValueWithUnits** | Numeric measurements with explicit distance units | `50 * millimeter`, `0.1 * meter` |
| **Angle / ValueWithUnits** | Rotational measurements with explicit angular units | `45 * degree`, `PI * radian` |
| **Boolean** | Boolean flag toggles | `true`, `false` |
| **String / Lookup** | Configuration labels, enums, and dropdown keys | `"LINEAR"`, `"DEFAULT"` |
| **Vector** | 2D or 3D positional/directional coordinates | `vector(0, 0, 0) * millimeter` |

### 5.3 Mathematical and Geometric Constants
- $\pi \ (\text{PI}) \approx 3.141592653589793$ (utilizing standard `PI` constant in FeatureScript math library).
- Unit conversion factors standard in metric SI (`meter`, `millimeter`, `degree`, `radian`).
- Tolerances aligned with OnShape CAD engine standard tolerances (`TOLERANCE` / Parasolid modeling resolution).

### 5.4 FeatureScript Core Operations & APIs
Library utilities will interface with standard OnShape FeatureScript APIs:

| FeatureScript API Operation | Description |
| :--- | :--- |
| `annotation { "Feature Type Name" : ... }` | Feature declaration and parameter UI definition |
| `newSketch()` / `newSketchOnPlane()` | Initializes sketch context on a selected or generated plane |
| `skLineSegment()` | Constructs linear sketch segments |
| `skArc()` / `skCircle()` | Constructs circular arcs or full circular curves |
| `skSolve()` | Solves and finalizes sketch geometry within Part Studio |
| `opBoolean()` | Performs solid boolean operations (union, subtract, intersect) |
| `opTransform()` | Applies spatial translations, rotations, and scaling transformations |
| `opCreate3dCurve()` / `opFitSpline()` | Generates 3D spatial curves |

---

## 6. Constraints and Limitations

### 6.1 Platform Constraints
- **Cloud-Only Execution:** All FeatureScript code executes within OnShape's cloud infrastructure. No offline or local CAD execution is supported.
- **Isolated Sandbox:** FeatureScripts cannot perform arbitrary OS-level system calls, open network sockets, access local filesystems, or integrate with external hardware/CAM peripherals.
- **Regeneration Lifecycle:** Scripts run strictly during feature regeneration upon user edits or upstream model updates.

### 6.2 FeatureScript Language Constraints
- **Entity Limits:** Sketch entities and features should be managed efficiently (typically recommended $< 100$ entities per sketch feature for interactive performance).
- **Recursion & Call Depth:** Nested recursion and call stacks are bounded by platform execution depth limits.
- **Third-Party Libraries:** Standard npm or external JavaScript packages cannot be imported; only OnShape-provided standard libraries or linked FeatureScript modules are permitted.
- **Memory Limits:** Execution memory allocation is restricted by platform caps (typically $< 256\text{ MB}$ per feature regeneration).

### 6.3 Geometric Constraints
- **Modeling Envelope:** Typical geometric dimensions constrained to practical CAD ranges (e.g., entity dimensions between $0.1\text{ mm}$ and $500\text{ mm}$).
- **Parameter Validation:** All numeric inputs must validate against negative or invalid dimensions to prevent CAD kernel topology failures.
- **Curve Approximation:** Non-analytical 3D curves require chordal error management to balance geometric fidelity with regeneration time.

### 6.4 Performance Constraints
- **Execution Timeout:** Features that exceed server-side processing limits will be aborted by the platform.
- **Sequential Regeneration:** OnShape regenerates features sequentially within the feature tree; algorithms must minimize expensive boolean operations.

---

## 7. Deliverables and Acceptance Criteria

### 7.1 Primary Deliverables
*None for the overall project.*

As a shared library project, there are no monolithic deliverables. Deliverables, scripts, and feature definitions are established on a per-sub-project basis.

### 7.2 Documentation Required
| Document Level | Purpose | Status |
| :--- | :--- | :--- |
| **L1 Project Definition** | Project overview, scope, and library architecture | Per Sub-Project |
| **L1 Sub-Project Definitions** | Scope and objectives for specific sub-projects | Per Sub-Project |
| **L2 Architecture Specifications** | System architecture, interfaces, and component boundaries | Per Sub-Project |
| **L3 Component Requirements** | Detailed specifications for individual library modules / components | Per Sub-Project |
| **L4/L5 Function Specs & Verification** | Low-level function contracts, algorithms, and validation suites | Per Sub-Project |

### 7.3 Acceptance Criteria
*Evaluated on a per-sub-project basis.*

Individual sub-projects will define their own verifiable acceptance criteria, test cases, and CAD regeneration benchmarks.

---

## 8. Requirements Traceability

In accordance with the Lightweight Development Process, this overall Library Project Definition (Level 1) serves as the umbrella under which sub-project requirements are organized:

```
[Level 1: Library Project Definition]
  └─ PD-000: OnShape FeatureScript Projects Library
       │
       └─► [Sub-Projects & Modular Requirements]
             ├─► [Level 1: Sub-Project Definitions (PD-xxx)]
             ├─► [Level 2: System & Architecture Requirements]
             │     └─ requirements/l2_architecture/
             ├─► [Level 3: Component Specifications]
             │     └─ requirements/l3_component/
             └─► [Level 4/5: Functional & Technical Implementation]
                   └─ requirements/l4l5_function_technical_implementation/
```
