# Generic scoop bucket

❗❗🎉 Repository was converted into Template. See [blog](https://github.blog/2019-06-06-generate-new-repositories-with-repository-templates/?utm_campaign=1559837005&utm_medium=social&utm_source=twitter&utm_content=1559837005) for more information. 🎉❗❗

In this repository you will find everything you need to know about creating custom bucket with appveyor support.

## Files and helpers

### `bucket` Folder

- All manifests belong here
- `.gitkeep` file could be removed after you push your first manifest

### `.vscode` Folder

Contains all syntax highlighting, code formating, manifest creating tools you could use.

- Extensions
    - All extensions which will save your time while writing manifests are in recommended sections
    - You will be notified about installing them when you open project
- Settings
    - All settings are set to be compatible with Appveyor pipeline and upstream (official) repositories
        - No need to worry about formating restrictions between repositories.
- Code snippets
    - > Code snippets are templates that make it easier to enter repeating code patterns, such as loops or conditional-statements.
    - You could use workspace wide code snippets for speed up manifest creating
    - While editing json file write partitial name of snippet and press `tab`
    - Available Json snippets:
        - `app`
            - Create default manifest structure
        - `appArch`
            - Create default manifest structure with full acrchitecture
        - `arch`
            - Create only architecture property with 64bit and 32bit
        - `upAr`
            - Create autoupdate property with architecture
        - `persistCheck`
            - Installer / pre_install script for checking if file is already persisted or need to be created

### `bin` Folder

Scripts which will save you much time while debuging and writing manifests.
If you need help how to use them just run `Get-Help .\bin\<BINARY>.ps1`.

### `Scoop-Bucket.Tests.ps1` File

- Test which are executed inside Appveyor pipeline
- Also are executed as `pre-commit` hook

### `config files`

- `.appveyor.yml`
    - Definition of Appveyor CI pipeline
- `.editorconfig`
    - Universal configuration file, compatible with all types of editors
    - Defines how files should look
- `.gitattributes`
    - Simplifying line endings for git
    - No need to configure `auto.clrf` setting on each clone or new workspaces

## How to use and adopt this bucket

1. Fork / Clone this repository
    - Cloning manually as zip is preferred as you will have `issues` available for your bucket
        - You can always add upstream repository using command line (see Step 8)
1. Give your bucket in new name inside github project settings
1. Add proper description of repository
    - Information about what type of manifests could be found here
1. Add `scoop-bucket` tag for repository
    - Your manifests will be automatically available at <https://scoop.netlify.com/apps/> and <https://scoop.netlify.com/buckets/>
1. Enable appveyor CI/CD
    1. Register / Login to [Appveyor](https://ci.appveyor.com/login)
    1. Click `New Project`
    1. From Left Panel choose your source control variant (Github)
    1. From Right Panel choose repository with bucket and click `+ Add`
    1. 🎉 Project created and ready to build 🎉
    1. Get Badge URL
        1. Open Appveyor Project settings
        1. Navigate to Badges
        1. Copy `Branch Sample markdown code` snippet for further usage
            - Only master branch is better, since you can freely test in other branches and do not mystificate users.
1. Clone project into some folder
1. Open vscode with this clone
1. Run `git remote add 'upstream' 'https://github.com/Ash258/GenericBucket.git'`
    - This step will allow you to synchronize changes with this template repository
    - If some changes are pushed into this repository and you want to reflect them into your bucket, you can simply do something like:
        - `git fetch --all`
        - `git checkout -B upstream-master -t upstream/master`
        - Do changes
        - `git merge master` or create PR in github
1. Create proper README.md
    1. Open `README.template.md`
    1. Replace all `%%templatestring%%` with real and according values
        1. Replace appveyor status badge with yours
            - See: <https://www.appveyor.com/docs/status-badges/>
    1. Override this README with completed `README.template.md`
    1. Remove template `README.template.md`
1. 🎉🎉 Everything set. You are ready to write and share manifests. 🎉🎉
