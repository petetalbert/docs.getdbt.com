---
title: "Implementing your mesh plan"
description: Getting started with dbt Mesh patterns
hoverSnippet: Learn how to get started with dbt Mesh
---

## Implementing a dbt Mesh

Let's examine an outline of steps to start implementing a dbt Mesh in your organization.

### Research your current structure

- Look at your selectors to figure out how people are grouping models right now.
- Talk to teams about what sort of separation is naturally existing right now
  - Are there various domains people are focused on?
  - Are there various sizes, shapes, and sources of data that get handled separately (such as click event data)?
  - Are there people focused on separate levels of transformation, such as landing and staging data or building marts?

## Add groups and access

Once you have a sense of some initial groupings, implement group and access permissions within a project.

- Incrementally start building your jobs based on these groups (we would recommend in parallel to your production jobs until you’re sure about them) to feel out that you’ve drawn the lines in the right place.

## Do the splits

- When you’ve confirmed the right groups, use `dbt-meshify` to pull chunks out into their own projects.
  - Do _one_ group at a time, using the groups as your selectors.
  - Do _not_ refactor as you migrate, however tempting that may be. Focus on getting 1-to-1 parity and log any issues you find in doing the migration for later. Once you’ve fully landed the project then you can start optimizing it for its new life as part of the mesh.