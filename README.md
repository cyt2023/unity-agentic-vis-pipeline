# Immersive TaxiVis / Agentic Visualization Pipeline

## Overview

This repository is built on top of the original *Immersive TaxiVis* Unity research prototype and extends it into an agentic, JSON-driven visualization pipeline.

The current work keeps the original project’s most important visualization-core ideas:
- OD trip data as the main data model
- Space-Time Cube style view construction
- coordinated point, link, and projection views
- query and filter driven visual updates
- Adapted IATK as the rendering foundation

On top of that base, this version adds a workflow execution path so that standardized EvoFlow-style JSON can be read inside Unity, resolved to local data, executed through a runtime operator chain, and then rendered through the existing frontend pipeline.

## Original Project Reference

This project is based on the original *Immersive TaxiVis* work by the paper authors.

Relevant references:
- Original research paper preprint: https://arxiv.org/abs/2402.00344
- Supplementary video: https://www.youtube.com/watch?v=5nQFVHqUBaU
- Original *TaxiVis* system: https://github.com/VIDA-NYU/TaxiVis

The current repository is an adaptation and extension of that original Unity prototype, rather than a new project from scratch.

## Current Scope

The current repository focuses on the visualization core and the new agentic workflow layer.

In particular, the current extension emphasizes:
- standardized workflow JSON input
- Unity-side data-path resolution
- runtime operator execution
- backend-result adaptation
- reuse of the existing Unity rendering path

The current focus is not on restoring the original immersive shell features such as VR interaction, maps, MRTK workflows, or Bing Maps integration.

## Current Agentic Workflow Path

The current execution path is:

`workflow JSON -> data path resolution -> runtime operator execution -> backend-result adaptation -> existing Unity renderer`

Primary integrated test assets:
- `Assets/StreamingAssets/test3_workflow.json`
- `Assets/StreamingAssets/demo_data/hurricane_sandy_2012_100k_sample.csv`
- `Assets/Scripts/Integration/Runtime/WorkflowRuntimeDemoController.cs`

## Main Runtime Additions

The main additions for the agentic workflow path are:
- `Assets/Scripts/WorkflowRuntime/*`
- `Assets/Scripts/Integration/Runtime/*`

These additions allow Unity to read an EvoFlow-style workflow description, execute the selected operator chain, and pass the result to the existing frontend rendering pipeline.

## How To Test The Current Workflow Path

Recommended environment:
- Unity 2022.1.10f1 or a closely compatible version
- Windows for final IATK-based rendering validation

Current test flow:
1. Open the Unity project.
2. Use the workflow runtime demo entry point in a scene.
3. Point it to `Assets/StreamingAssets/test3_workflow.json` or keep the default setting.
4. Run the scene.
5. Verify that Unity resolves the CSV path, executes the operator workflow, and renders the point-based result.

## Notes

This repository should be understood as an adaptation of the original *Immersive TaxiVis* codebase toward an agentic workflow execution model. The original project remains the conceptual basis; the current contribution is the workflow-oriented extension on top of that foundation.
