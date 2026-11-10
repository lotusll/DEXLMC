---
name: dexlmc-wp
description: 'Use when maintaining DEXLMC/LMC Work Package templates, adding or moving template Sub-tasks, managing DEXLMC components, or bringing Work Packages into a Country Launch. Triggers: DEXLMC, LMC, Work Package, Sub-task, Country Launch, Launch Master Checklist WP.'
---

# DEXLMC Work Package Skill

Use this workflow for repeatable maintenance of the DEX Launch Master Checklist (DEXLMC/LMC). Follow the source procedure in [DEXLMC maintenance and Tips&Tricks](https://confluence.build.ingka.ikea.com/spaces/DEXGOJIRA/pages/1301875356/DEXLMC+maintenance+and+Tips+Tricks). The Jira Kanban board is [DEX (Chapter) - Launch Master Checklist](https://jira.digital.ingka.com/secure/RapidBoard.jspa?rapidView=13502&projectKey=DEXLMC).

## Safety and scope

- Inspect the relevant Work Package, its children, project, component, labels, status, and parent before changing Jira.
- For a request to update an LMC template from a country Work Package, compare the child Sub-tasks first. Report missing, extra, and differing tasks. Confirm which changes to make when scope or applicability is unclear.
- Change only the requested template fields/tasks. Do not copy country statuses or overwrite existing template tasks unless explicitly requested.
- Do not infer that a parent-link change moves an issue between Jira projects. Cross-project issue moves are a distinct Jira operation and may require additional permissions.
- Check the current user's Jira permissions before attempting create/edit/move operations. If permission is absent, stop and give the project owner the precise requested change.
- Never delete a component or bulk-edit issues without explicit confirmation. Check component usage before proposing deletion.

## Components

Each Work Package needs a corresponding component:

- Create the component in **DEXLMC** so it can be set on the Work Package.
- Create the corresponding component in **DEX** so it can be added to a pEpic and used by Country Launch automation.
- In the project’s **Components** page, fill the component fields and set **Assignee** to **Project default**, then add it.
- To edit a component, find it on the Components page and use its **… → Edit** menu.
- Before deleting a component, check how many issues use it. If Jira prompts how to handle linked issues and the right choice is uncertain, choose **Remove the component from all issues**, not an unverified replacement.

## Update an existing Sub-task or Work Package

1. Open the DEXLMC Kanban board and locate the relevant Work Package and Sub-task.
2. Open the issue card or issue in a separate window.
3. Make the requested field changes in the issue details panel or issue page.
4. Verify the saved values on the issue.

## Add a Sub-task to an existing Work Package

1. Open the Work Package on the DEXLMC board.
2. Open one of its existing Sub-tasks, then navigate back to the Work Package.
3. Clone an existing Sub-task from the Work Package’s child list.
4. Update the clone to fit the new task, including its summary, description, labels, component, and other explicitly requested fields.
5. Confirm the new issue is a Sub-task under the intended Work Package and that it appears on the board when eligible.

When adding a task to the reusable template based on a country Work Package:

1. Compare the source and template children by task summary, not just child count.
2. Confirm that a country-only task is appropriate for the reusable template before adding it.
3. Follow the established template pattern: use the **DEXLMC** project, Sub-task issue type, the target Work Package as parent, and that Work Package’s component.
4. Preserve source task instructions and labels when they are applicable to all launches. Do not propagate country-specific status, assignee, or other values unless requested.
5. Verify the resulting parent, component, labels, description, status, and board eligibility.

## Move a Sub-task to a different Work Package

1. Open the current parent Work Package and its Sub-task.
2. Open the Sub-task in a separate window.
3. Change the Sub-task’s **Component** to the destination Work Package’s component.
4. Choose **More → Move**.
5. Select **Change parent**, choose the destination Work Package, and complete the Jira move flow.
6. Verify both the new parent and component.

This procedure is for moving a **Sub-task** between Work Packages. Do not assume it applies to moving a Work Package between projects.

## Add a Work Package

1. From the DEXLMC Kanban board, use **Create** to make a Work Package, or clone an existing Work Package.
2. If cloning, leave **Clone sub-tasks** and **Clone links** unchecked unless the user specifically requests them.
3. Set the correct component and labels.
4. Verify the issue type, project, component, labels, and parent/launch association.

## Bring template Work Packages into a Country Launch

Normally, use the existing pEpic/Country Launch relationship and the project components and automation configured for that launch. The following workaround is only for a Country Launch that has **no parent pEpic**:

1. On the Country Launch, ensure its Component field is empty.
2. Set **Local/Central** to **Digital Expansion**.
3. Temporarily set the Country Launch Parent Link to **DEX-1**.
4. Open [DEX-1](https://jira.digital.ingka.com/browse/DEX-1), remove all existing Component values, and add only the components to bring into the Country Launch.
5. Return to the Country Launch and run the **Launch Master Checklist WP** automation.
6. Reload and verify that the expected Work Packages and their Sub-tasks were imported.
7. Clean up: return to DEX-1 and remove the temporary components; return to the Country Launch and remove its temporary Parent Link to DEX-1.

Do not use this workaround when the Country Launch already has a pEpic. Verify the automation result before cleanup; if the expected Work Packages were not imported, stop and investigate rather than assuming success.

## Board and verification notes

- The board is a Kanban board based on a saved filter plus a subquery; not every issue in a project necessarily appears on it.
- The current board filter is scoped to DEXLMC/LMC Sub-tasks and excludes Invalid issues; its subquery includes issues with unreleased or empty fix versions. Check the live board/filter if an issue does not appear.
- After any update, read the issue back and verify the requested fields, parent/component relationship, and board visibility where relevant.
