# Reproduce

        git worktree add foo
        cd foo
        git submodule update --init
        cd GitVersion
        dotnet-gitversion.exe

# Output

      INFO [04/12/22 16:55:09:61] Working directory: D:\vfs\mwe-gitversion-bug\mwe-gitversion-bug\foo\GitVersion
      INFO [04/12/22 16:55:09:63] Project root is: D:\vfs\mwe-gitversion-bug\mwe-gitversion-bug\foo\GitVersion\
      INFO [04/12/22 16:55:09:63] DotGit directory is: D:\vfs\mwe-gitversion-bug\mwe-gitversion-bug\.git\worktrees\foo
      ERROR [04/12/22 16:55:09:65] An unexpected error occurred:
      System.IO.DirectoryNotFoundException: Root directory does not exist: D:\vfs\mwe-gitversion-bug\mwe-gitversion-bug\.git\worktrees\foo\refs
         at GitVersion.VersionCalculation.Cache.GitVersionCacheKeyFactory.CalculateDirectoryContents(String root) in D:\a\GitVersion\GitVersion\src\GitVersion.Core\VersionCalculation\Cache\GitVersionCacheKeyFactory.
      cs:line 69
         at GitVersion.VersionCalculation.Cache.GitVersionCacheKeyFactory.GetGitSystemHash() in D:\a\GitVersion\GitVersion\src\GitVersion.Core\VersionCalculation\Cache\GitVersionCacheKeyFactory.cs:line 53
         at GitVersion.VersionCalculation.Cache.GitVersionCacheKeyFactory.Create(Config overrideConfig) in D:\a\GitVersion\GitVersion\src\GitVersion.Core\VersionCalculation\Cache\GitVersionCacheKeyFactory.cs:line 39
         at GitVersion.GitVersionCalculateTool.CalculateVersionVariables() in D:\a\GitVersion\GitVersion\src\GitVersion.Core\Core\GitVersionCalculateTool.cs:line 47
         at GitVersion.GitVersionExecutor.RunGitVersionTool(GitVersionOptions gitVersionOptions) in D:\a\GitVersion\GitVersion\src\GitVersion.App\GitVersionExecutor.cs:line 70
      INFO [04/12/22 16:55:09:65] Attempting to show the current git graph (please include in issue):
      INFO [04/12/22 16:55:09:65] Showing max of 100 commits
      INFO [04/12/22 16:55:09:72] * c3e943b2f 23 hours ago  (origin/dependabot/github_actions/actions/cache-3.0.2)
      * 6ef2aad72 5 days ago  (HEAD, origin/support/5.x, origin/HEAD, support/5.x)
      | *   9e71251e3 6 days ago  (origin/main)
      | |\
      | |/
      |/|
      * |   b6015683c 8 days ago
      |\ \
      | * | c6fefe1a3 8 days ago
      | * | 03b29d1e5 8 days ago
      | * | c0e139a15 8 days ago
      [...]

DotGit is: `D:\vfs\mwe-gitversion-bug\mwe-gitversion-bug\.git\worktrees\foo`, but `D:\vfs\mwe-gitversion-bug\mwe-gitversion-bug\foo\GitVersion\.git` contains `gitdir: ../../.git/worktrees/foo/modules/GitVersion`

DotGit should be `D:\vfs\mwe-gitversion-bug\mwe-gitversion-bug\.git\worktrees\foo/modules/GitVersion`