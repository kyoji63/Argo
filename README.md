# 🐝 Argo
# Abstract
GitHub, with its vast repository count of over 10 million, attracts researchers interested in mining software repositories. Analyzing and investigating GitHub repositories can provide valuable insights for improving software development activities. However, there is currently no standardized method for accessing source code change histories and communication histories.

This paper presents the implementation of a tool called "argo" that aims to fetch communication histories from GitHub. Argo accepts users' GraphQL queries to retrieve communication histories recorded on GitHub and generates line charts to visualize their transitions. As a case study, we implemented three types of GraphQL queries to fetch data on stargazers, issues, and pull requests from 11 repositories of famous programming languages hosted on GitHub.

Using Argo, we were able to fetch data at an impressive rate. The number of entries per second for stargazers, issues, and pull requests was 145.19, 81.27, and 139.90, respectively. Among the repositories, fetching stargazers' data for the repository "golang/go" proved to be the most time-consuming, with 96,425 entries requiring 716 seconds.

In conclusion, we demonstrated that our tool, Argo, can successfully fetch data from GitHub and generate line charts based on the retrieved information.

## Setting Personal Access Tokens
The personal access tokens for Star.py, Issue.py, and PullRequest.py in the query directory must be set before it will work.
The user can set them on the command line.

# About
## License
[GNU General Public License version 3 (GPLv3)](https://www.gnu.org/licenses/gpl-3.0.ja.html)

## Logo  
![Honey_Bee_logo__4_-removebg-preview](https://github.com/kyoji63/Argo/assets/69036517/9af5899a-e61c-4472-8b28-ec89f746b04a)

## Project name comes from?
Abbreviation for Auto Repository Graph Output.
The logo of "Argo" is a bee icon from Argogorytes. 

# I/O Specifications
## 🏃‍♀️ Usage

```sh
argo [GLOBAL_OPTIONS] <COMMAND> [<ARGS>]
GLOBAL_OPTIONS
    -c, --config <CONFIG>    specify configuration file path.
    -h, --help               print this message.
COMMANDs
    help          print help message.
    fetch         fetch data from GitHub.
    draw          draw line chart from fetched data.
    list          list available queries and metrics.
    fetch-draw    fetch data and draw line chart.
```

### `argo fetch`

```sh
argo fetch [OPTIONS] <ARGS...>
OPTIONS
    -q, --query <QUERY>           specify the query. This option is mandatory.

    -c, --cache-dir <DIR>         specify the cache directory path.
        --ignore-cache            ignore the stored cache data.
        --no-cache                no cache the fetched data.
    -Q, --queries-dir <DIR>       specify the directory contains GraphQL queries.
ARGS
    specify GitHub repository by owner/name format.
```

### `argo draw`

```sh
argo draw [OPTIONS] <ARGS...>
    -m, --metric <METRIC>      specify the metric (chart script). This option is mandatory.

    -c, --cache-dir <DIR>      specify the cache directory path.
        --ignore-cache         ignore the stored cache data.
        --no-cache             no cache the fetched data.
    -d, --write-data <DEST>    set file name of graph data destination. if this option is absent, argo outputs no graph data.
    -f, --format <FORMAT>      specify the output image format. available: pdf, svg, and png. default: svg.
    -M, --metrics-dir <DIR>    specify the directory contains chart scripts.
    -u, --unit <UNIT>          specify the unit time. Default is 1M.
                               Available: nD, nW, nM, and nY. n is the integer number,
                                          D, W, M, Y means day, week, month, and year, respectively.
ARGS
    specify GitHub repository by owner/name format.
```

### `argo list`

```sh
argo list
    -M, --metrics-dir <DIR>    specify the directory contains chart scripts.
    -Q, --queries-dir <DIR>    specify the directory contains GraphQL queries.
```


### structure of `~/.config/argo` directories.

```sh
.config/argo
├── caches
│   ├── microsoft
│   │   └── vscode
│   │       ├── issues
│   │       ├── pullrequests
│   │       └── stargazers
│   └── ruby
│       └── ruby
├── config
│   └── default.json
├── metrics
│   ├── microsoft
│   │   └── vscode
│   │       ├── N-STAR
│   │       └── R-RIS
│   └── ruby
│       └── ruby
├── scripts
│   ├── LT-CIS.awk
│   ├── LT-RP.py
│   ├── N-RIS.rb
│   ├── N-STAR.py
│   ├── R-MGPR.py
│   ├── R-PRLP.py
│   └── R-RIS.py
└── queries
    ├── issues.graphql
    ├── pullrequests.graphql
    └── stargazers.graphql
```

## Output
### fetch data
```
First Survey
200it [00:00, 1835581.62it/s, 2]                                                

200it [00:00, 1536375.09it/s, 2]                                                

Data acquisition completed! : 1.4907136
```
### draw chart
- Eight metrics were drawn for 11 programming languages published on GitHub.

<img src = "https://user-images.githubusercontent.com/69036517/172577380-d8397972-693c-40a3-b460-7d4c8f3ccafb.png" width = "320px"> <img src = "https://user-images.githubusercontent.com/69036517/172577395-17243e2b-1b8c-4109-a405-afec7275a636.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577273-31b4ee49-9f78-44ba-837d-fa293f417d36.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577456-dca4392f-6149-4c07-b031-f6442bc68a7f.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577369-112cd315-dc87-4f2d-8573-61416714478f.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172580845-a21aa26d-28d0-4f49-9205-2d59f04ed5a7.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577424-2e8cd21a-803a-47da-a59b-9639ba2f2a4a.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172581269-4924a22b-3c83-4405-92bc-5301a8ee3932.png" width = "320px">
