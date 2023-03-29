# nginx-semantic-tag

1. Allow Read and Write workflow permissions to Github action from settings -> actions -> workflow permission 

2. Add AWS ACCESS KEY and SECRET ACCESS KEY to repo

3. Add initial tag to repo
    1. git tag v0.0.0 -m "Initial tag added"
    2. git push origin v0.0.0
    3. git push origin
    4. git pull

4. to get semantic versioning , commit and push the changes as per below format (should generate docker image)
    1. git commit -m "message  <#version_update> -> 
        1. #patch -> for patch update -> v0.0.X
        2. #minor -> for minor update -> v0.X.0
        3. #major -> for major update -> vX.0.0

null

======================================================================

Options
Environment Variables

GITHUB_TOKEN (required) - Required for permission to tag the repo.
DEFAULT_BUMP (optional) - Which type of bump to use when none explicitly provided (default: minor).
DEFAULT_BRANCH (optional) - Overwrite the default branch its read from Github Runner env var but can be overwritten (default: $GITHUB_BASE_REF). Strongly recommended to set this var if using anything else than master or main as default branch otherwise in combination with history full will error.
WITH_V (optional) - Tag version with v character.
RELEASE_BRANCHES (optional) - Comma separated list of branches (bash reg exp accepted) that will generate the release tags. Other branches and pull-requests generate versions postfixed with the commit hash and do not generate any tag. Examples: master or .* or release.*,hotfix.*,master ...
CUSTOM_TAG (optional) - Set a custom tag, useful when generating tag based on f.ex FROM image in a docker image. Setting this tag will invalidate any other settings set!
SOURCE (optional) - Operate on a relative path under $GITHUB_WORKSPACE.
DRY_RUN (optional) - Determine the next version without tagging the branch. The workflow can use the outputs new_tag and tag in subsequent steps. Possible values are true and false (default).
INITIAL_VERSION (optional) - Set initial version before bump. Default 0.0.0.
TAG_CONTEXT (optional) - Set the context of the previous tag. Possible values are repo (default) or branch.
PRERELEASE (optional) - Define if workflow runs in prerelease mode, false by default. Note this will be overwritten if using complex suffix release branches.
PRERELEASE_SUFFIX (optional) - Suffix for your prerelease versions, beta by default. Note this will only be used if a prerelease branch.
VERBOSE (optional) - Print git logs. For some projects these logs may be very large. Possible values are true (default) and false.
MAJOR_STRING_TOKEN (optional) - Change the default #major commit message string tag.
MINOR_STRING_TOKEN (optional) - Change the default #minor commit message string tag.
PATCH_STRING_TOKEN (optional) - Change the default #patch commit message string tag.
NONE_STRING_TOKEN (optional) - Change the default #none commit message string tag.
BRANCH_HISTORY (optional) - Set the history of the branch for finding #bumps. Possible values last, full and compare defaults to compare.
full: attempt to show all history, does not work on rebase and squash due missing HEAD [should be deprecated in v2 is breaking many workflows]
last: show the single last commit
compare: show all commits since previous repo tag number