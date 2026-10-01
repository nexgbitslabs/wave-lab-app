# ChatGPT to Wave Migration

Migrate this repository from its existing Jenkins-based delivery implementation
to the Wave Lab GitHub Actions platform.

## Instructions

Use the Wave Lab migration instructions:

`instructions/chatgpt-to-wave-migration.instructions.md`

Use the Wave Lab standards repository as the authoritative migration source:

https://github.com/nexgbitslabs/wave-lab-wave.git

Obtain and read that repository before generating migration changes.

Use it as the authoritative source for:

- workflow capabilities;
- Jenkins-to-Wave mappings;
- repository parameter structure;
- reusable Wave workflows;
- migration rules.

Treat the Wave Lab standards repository as read-only reference material.
Do not modify it during this migration.

## Required Process

1. Analyze the repository before making changes.

2. Inspect all Jenkins artifacts, including:
   - Jenkinsfiles;
   - Jenkins properties;
   - pipeline parameters;
   - environment variables;
   - credential references;
   - Docker operations;
   - Terraform operations;
   - GitOps operations.

3. Map discovered Jenkins behavior using:

   `mappings/jenkins-to-wave-mapping.yaml`

4. Select only capabilities defined in:

   `docs/workflow-catalog.md`

5. Generate the required Wave-compatible GitHub Actions workflows under:

   `.github/workflows/`

6. Generate:

   `repository-parameters.yaml`

   according to:

   `docs/repository-parameters.md`

7. Do not copy Jenkins secret values.

8. Preserve explicit Terraform lifecycle separation:
   - initialize
   - plan
   - apply
   - destroy

9. Preserve the GitOps deployment model.

   Application deployment must remain:

   CI
   -> ACR
   -> GitOps repository
   -> Flux v2
   -> AKS

   Do not introduce direct application deployment to AKS.

10. Create the migration branch:

    `feature/chatgpt-to-wave-migration`

11. Generate:

    `wave-migration-report.md`

12. Validate the generated migration before reporting completion.

## Important

Do not invent missing Wave capabilities or configuration.

If behavior cannot be mapped, document it for human review rather than silently
discarding or replacing it.

Do not modify the default branch directly.