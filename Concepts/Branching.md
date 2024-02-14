[[_TOC_]]

# Branching
- Have a main branch for CI to share changes between developers 
  - call it whatever you want (e.g. master)
- Each developer branch from the latest main to make changes
- Changes are then merged back to main branch via CI 

During this process, the main branch should always be production ready. Branch policies may be used to protect the quality of the main branch. However, there are options in how branching can happen to allow sharing of changes between developers, and to facilitate release to production.

## Principles
- Keep it simple
  - branching should be easy to use for all developers/tester/pipeliners/infras involved
  - simplify code sharing and collaboration so the process is efficient
  - it is not painful to merge where the smaller the logical chunk the better
- Support continuous delivery
  - build trust on the path to production
  - quality focused with built-in tests along the way
  - increase confidence with practice on releases using the same set of artifacts and deployment steps
  - support an efficient, speedy release cycle

## Branch Policies
- Leverage automated checks to protect the main branch
  - there are ways to increase confidence in the changes merged to the main branch including 
    - required code reviews 
    - required approvers
    - required builds pass
    - required change traceability (change legitimacy)

## Naming convention
- It is recommended to have some naming convention in the creation of branches. This facilitates the maintenance and provide visibility of the usage of these branches. 
- Common organization structure
  - _main_ branch is often the main branch residing at the root level
    - root level branches are considered important branches
  - _feature/user/workitemID-description_ are often used to house work that is happening during a sprint
    - these are folder level branches that should be very short-lived
  - _release/releasename_ may be used in branching strategy that requires a longer-living branch (more than a sprint, perhaps per quarterly release cycle) 

# Branching Methods

## Trunk-based
https://trunkbaseddevelopment.com/
- feature branches are created per logical chunk of change and they are very short lived
- main branch is always production ready
- release branches may be created from the main branch for just-in-time release but not long living
- no long running branches except for the trunk
- good for scaling to larger teams for more frequent CI will happen at the main branch

![image.png](/.attachments/image-d2516fbd-4c90-428f-a175-831d596702ae.png)

## GitHub flow
https://guides.github.com/introduction/flow/
- feature branches are created per logical chunk of change and they are very short lived
- similar to trunk based, the main branch is always production ready
- release from the feature branch before merging to main, once deployment is successful in production, changes are merged to main
- no long running branches except for the trunk
- good for small teams when there is no need to race to main branch

![image.png](/.attachments/image-fd3b34ef-1418-49db-ac44-9f3e95f40710.png)

## git-flow
https://nvie.com/posts/a-successful-git-branching-model/
- feature branches are created per logical chunk of change and they are very short lived
- main branch is the source of truth for the latest, but it is not used for releases
- release branches are created for releases
- a long running develop branch is used for sprint development
- has become less adopted in recent years compared to trunk-based due to potential large divergence between main and develop

![image.png](/.attachments/image-5f8c4d62-d024-4c0c-9108-8b89670915b6.png)

