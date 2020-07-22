# sheat
```
+-----------------------------+-----------------------------------------------------+
| General Parameters          | Description                                         |
+-----------------------------+-----------------------------------------------------+
| -v, --verbose               | Verbose mode (More output)                          |
| -q,--quietQuiet             | mode (Less output)                                  |
| -h,--help                   | Help/Options                                        |
| -V,--version                | Display version info                                |
| --isolated                  | Ignore environment variables and user configuration |
| --log PATH                  | Log file                                            |
| --proxy PROXY               | USER:PSWD@SERVER:PORT                               |
| --retries X                 | Retry connection X times                            |
| --timeout SECONDS           | Try for X seconds before retry                      |
| --cache-dir DIR             | Cache directory                                     |
| --no-cache-dir              | Disable cache                                       |
| --disable-pip-version-check | Do not check Pip version                            |
| --cert PATH                 | Path to secondary CA bundle                         |
| --client-cert CERT          | Path to SSL certificate                             |
| --trusted-host HOSTNAME     | Consider the host trusted                           |
+-----------------------------+-----------------------------------------------------+
| List                        | Description                                     |
+-----------------------------+-------------------------------------------------+
| pip list                   | List packages-o,                                 |
| --outdated                 | List outdated packages-u,                        |
| --uptodate                 | List current packages-e,                         |
| --editable                 | List editable items-l,                           |
| --local                    | List local virtualenv packages                   |
| --user                     | List user-site packages                          |
| --pre                      | Include developmental packages-i URL,            |
| --index-url                | URLPyPI URL                                      |
| --extra-index-url          | URL Additional package repos                     |
| --no-indexIgnore package   | index-f URL,                                     |
| --find-links               | URL Search for archives at the URL               |
| --allow-external PKG       | Allow package installation                       |
| --allow-all-external       | Allow externally hosted packages to be installed |
| --allow-unverified PKG     | Install insecure package                         |
| --process-dependency-links | Process links for dependencies                   |
+-----------------------------+-------------------------------------------------+
| Show                        | Description                                     |
+-----------------------------+-------------------------------------------------+
| pip show PKG       | Display package info-f, |
| --filesList        | package's               |
| filesSearch        | Description             |
| pip search KEYWORD | Search PyPI for keyword |
| --index URL        | Repo to search          |
+-----------------------------+----------------+
| Uninstall                   | Description    |
+-----------------------------+------------------------------------------------+
| pip uninstall               | PKGUninstall/remove package                    |
| -r FILE  --requirement FILE | Uninstall packages listed in requirements file |
| -y, --yesAssume             | “yes” for questions                            |
+-----------------------------+------------------------------------------------+
| Freeze                      | Description                                    |
+-----------------------------+------------------------------------------------+
| pip freeze Generate | requirements file-r FILE,              |
| --requirement FILE  | Use the order given in the file-f URL, |
| --find-links URL    | URL for finding packages-l,            |
| --localOnly list    | virtualenv packages                    |
| --userOnly list     | user-site packages                     |
+-----------------------------+--------------------------------------------------+
| Install                     | Description                                      |
+-----------------------------+--------------------------------------------------+
| pip install PKG             | Install package                                  |
| pip install PKG==1.0        | Install specific version                         |
| pip install 'PKG>=1.0'      | At least, install version X                      |
| -r FILE, --requirement FILE | Install listed packages in the requirements file |
| -b DIR --build DIR          | Directory for building packages-t DIR,           |
| --target DIR                | Install in directory-d DIR                       |
| -d DIR, --download DIR      | Download only                                    |
| -U, --upgrade               | Update listed packages                           |
| --force-reinstall           | Re-install packages when updating                |
| -I --ignore-installed       | Re-install                                       |
| --no-deps                   | Do not install dependencies                      |
| --egg                       | Install as an Egg                                |
| --compile                   | Compile *.py to *.pyc                            |
| --no-compile                | Do not compile                                   |
| --no-use-wheel              | Do not use wheels                                |
| --preInclude                | developmental versions                           |
| --no-cleanDo                | not clean build directories                      |
| -i URL, --index-url         | URLPyPI URL                                      |
| --extra-index-url           | URL Additional URLs                              |
| --no-indexOnly              | use                                              |
| --find-links                | URLs -f URL,                                     |
| --find-links URL            | Parse links for archives                         |
| --allow-external PKG        | Install 3rd-party package                        |
| --allow-all-external        | Install 3rd-party packages                       |
| --allow-unverified PKG      | Install unverified package                       |
| --process-dependency-links  | Process links for dependencies                   |
+-----------------------------+--------------------------------------------------+
```
