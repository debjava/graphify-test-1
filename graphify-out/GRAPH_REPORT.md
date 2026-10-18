# Graph Report - graphify-test-1  (2026-10-18)

## Corpus Check
- cluster-only mode — file stats not available

## Summary
- 402 nodes · 1012 edges · 14 communities (8 shown, 6 thin omitted)
- Extraction: 97% EXTRACTED · 3% INFERRED · 0% AMBIGUOUS · INFERRED: 26 edges (avg confidence: 0.85)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- Community 0
- Community 1
- Community 2
- Community 3
- Community 4
- Community 5
- Community 6
- Community 7
- Community 8
- Community 9
- Community 10

## God Nodes (most connected - your core abstractions)
1. `CodePublishPanelComponent` - 38 edges
2. `UserAccount` - 32 edges
3. `IGitHandler` - 23 edges
4. `GitPanelComponent` - 20 edges
5. `GithubHandler` - 19 edges
6. `GitlabHandler` - 19 edges
7. `BitbucketHandler` - 19 edges
8. `GitUtil` - 18 edges
9. `CodeSharingDialog` - 17 edges
10. `GitOnlineResponse` - 15 edges

## Surprising Connections (you probably didn't know these)
- `ReadMeGenerator` --implements--> `IGenerator`  [EXTRACTED]
  ddlabs-gitifier/src/main/java/com/ddlab/rnd/generator/ReadMeGenerator.java → ddlabs-gitifier/src/main/java/com/ddlab/rnd/generator/IGenerator.java
- `GithubHandler` --references--> `UserAccount`  [EXTRACTED]
  ddlabs-gitifier/src/main/java/com/ddlab/rnd/github/GithubHandler.java → ddlabs-gitifier/src/main/java/com/ddlab/rnd/git/model/UserAccount.java
- `GitlabHandler` --references--> `UserAccount`  [EXTRACTED]
  ddlabs-gitifier/src/main/java/com/ddlab/rnd/gitlab/GitlabHandler.java → ddlabs-gitifier/src/main/java/com/ddlab/rnd/git/model/UserAccount.java
- `BitbucketHandler` --references--> `UserAccount`  [EXTRACTED]
  ddlabs-gitifier/src/main/java/com/ddlab/rnd/handler/bitbucket/BitbucketHandler.java → ddlabs-gitifier/src/main/java/com/ddlab/rnd/git/model/UserAccount.java
- `GithubHandler` --implements--> `IGitHandler`  [EXTRACTED]
  ddlabs-gitifier/src/main/java/com/ddlab/rnd/github/GithubHandler.java → ddlabs-gitifier/src/main/java/com/ddlab/rnd/handler/IGitHandler.java

## Import Cycles
- None detected.

## Communities (14 total, 6 thin omitted)

### Community 0 - "Community 0"
Cohesion: 0.08
Nodes (9): BitbucketRepoInput, BadCredentialsException, ReadMeGenerator, GitOnlineErrorResponse, GitOnlineResponse, UserAccount, HostedRepo, ConfigReaderUtil (+1 more)

### Community 1 - "Community 1"
Cohesion: 0.07
Nodes (7): HostedGitType, BITBUCKET, GITHUB, GITLAB, IGitHandler, CodeSharingUtil, GitUtil

### Community 2 - "Community 2"
Cohesion: 0.07
Nodes (7): TestButtonServiceImpl, Task.Modal, PublisherSettingConfig, ActionListener, GitPanelComponent, JTable, UIUtil

### Community 3 - "Community 3"
Cohesion: 0.08
Nodes (4): MessageBundle, RepoExistException, PublisherSetting, CommonUIUtil

### Community 4 - "Community 4"
Cohesion: 0.12
Nodes (4): GithubHandler, GitlabHandler, GitLabRepo, BitbucketHandler

### Community 5 - "Community 5"
Cohesion: 0.08
Nodes (4): ComboBoxRenderer, DeleteButtonRenderer, DeleteCellEditor, TextCellRenderer

### Community 6 - "Community 6"
Cohesion: 0.10
Nodes (5): GitIgnoreGenerator, IGenerator, Task.Backgroundable, Task.Backgroundable, GeneratorUtil

### Community 9 - "Community 9"
Cohesion: 0.29
Nodes (5): BitbucketClone, BitbucketOutputRepo, BitbucketRepoLink, Repo, GitHubRepo

## Knowledge Gaps
- **6 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `CodePublishPanelComponent` connect `Community 7` to `Community 0`, `Community 1`, `Community 2`, `Community 3`, `Community 8`, `Community 9`?**
  _High betweenness centrality (0.147) - this node is a cross-community bridge._
- **Should `Community 0` be split into smaller, more focused modules?**
  _Cohesion score 0.08090117767537122 - nodes in this community are weakly interconnected._
- **Why does `GitPanelComponent` connect `Community 2` to `Community 0`, `Community 9`, `Community 3`, `Community 5`?**
  _High betweenness centrality (0.112) - this node is a cross-community bridge._
- **Should `Community 1` be split into smaller, more focused modules?**
  _Cohesion score 0.06753246753246753 - nodes in this community are weakly interconnected._
- **Why does `UserAccount` connect `Community 0` to `Community 1`, `Community 2`, `Community 3`, `Community 4`?**
  _High betweenness centrality (0.103) - this node is a cross-community bridge._
- **Should `Community 2` be split into smaller, more focused modules?**
  _Cohesion score 0.07164404223227752 - nodes in this community are weakly interconnected._
- **Should `Community 3` be split into smaller, more focused modules?**
  _Cohesion score 0.07770582793709528 - nodes in this community are weakly interconnected._