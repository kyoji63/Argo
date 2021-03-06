# ð Argo
# æ¦è¦
è¿å¹´ãéçºèèªèº«ãèªçºçã«ææ¡ã§ããã½ã¼ã·ã£ã«ã³ã¼ãã£ã³ã°ã¨ããæ°ããªã½ããã¦ã§ã¢éçºæ¹å¼ã«æ³¨ç®ããã¦ãããããããªãããç¾ç¶ã®ãèªçºçã½ããã¦ã§ã¢é²åããè¾¿ã£ã¦ããæåãã­ã¸ã§ã¯ããã©ã®ããã«ç®¡çãããæ´»çºãªã³ãã¥ããã£ãã©ã®ããã«å½¢æããã¦ãããåãããªãã

æ¬ç ç©¶ã§ã¯ãããå¤ãã®ãã­ã¸ã§ã¯ãã«å¯¾ãã¦åæ§ã®èª¿æ»ãè¡ããèªçºçé²åã®è¯ããã¿ã¼ã³ã»æªããã¿ã¼ã³ãçºè¦ããã©ããæ¹åãããããèªçºé²åãè¦è¾¼ããã®ããææ¡ãããã¨ãç®çã¨ããã
ããããç¾ç¶ã§ã¯GraphQLãç¨ãããã¼ã¿æ½åºã«ã¯çµæ§ãªå´åãå¿è¦ã¨ãªããããã¾ããã¼ã¿åæãèªååããã¢ããªã±ã¼ã·ã§ã³ãä½æããã

## åäººã¢ã¯ã»ã¹ãã¼ã¯ã³ã®è¨­å®
queryãã£ã¬ã¯ããªã«ããStar.py, Issue.py, PullRequest.pyã®åäººã¢ã¯ã»ã¹ãã¼ã¯ã³ãè¨­å®ããªãã¨åããªãï¼
userå´ããã³ãã³ãã©ã¤ã³ã§è¨­å®ã§ããããã«ããï¼

# About
## License
[GNU General Public License version 3 (GPLv3)](https://www.gnu.org/licenses/gpl-3.0.ja.html)

## Logo  
<img src = "https://user-images.githubusercontent.com/69036517/122642836-6017fc80-d147-11eb-8717-5d5664b589aa.png"
     width = "320px">

pngtreeããå¼ç¨.
https://ja.pngtree.com/freepng/bee-animal-icon-honey-flying-bee-insect-bugs_3641499.html

## Project name comes from?
Argogorytesï¼ã¢ã¯ãã­ããï¼ããèã®ã¢ã¤ã³ã³ã«ãã. 

# å¥åºåä»æ§
## Usage

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
âââ caches
âÂ Â  âââ microsoft
âÂ Â  âÂ Â  âââ vscode
âÂ Â  â       âââ issues
âÂ Â  â       âââ pullrequests
âÂ Â  âÂ Â      âââ stargazers
âÂ Â  âââ ruby
âÂ Â      âââ ruby
âââ config
âÂ Â  âââ default.json
âââ metrics
âÂ Â  âââ microsoft
âÂ Â  âÂ Â  âââ vscode
âÂ Â  â       âââ N-STAR
âÂ Â  âÂ Â      âââ R-RIS
âÂ Â  âââ ruby
âÂ Â      âââ ruby
âââ scripts
â   âââ LT-CIS.awk
â   âââ LT-RP.py
â   âââ N-RIS.rb
â   âââ N-STAR.py
â   âââ R-MGPR.py
â   âââ R-PRLP.py
â   âââ R-RIS.py
âââ queries
    âââ issues.graphql
    âââ pullrequests.graphql
    âââ stargazers.graphql
```

## åºå
### fetch data
```
First Survey
200it [00:00, 1835581.62it/s, 2]                                                

200it [00:00, 1536375.09it/s, 2]                                                

Data acquisition completed! : 1.4907136
```
### draw chart
- GitHubã§å¬éããã¦ãã11ã®ãã­ã°ã©ãã³ã°è¨èªãå¯¾è±¡ã«ï¼ã¤ã®ã¡ããªã¯ã¹ãæç»ããï¼

<img src = "https://user-images.githubusercontent.com/69036517/172577380-d8397972-693c-40a3-b460-7d4c8f3ccafb.png" width = "320px"> <img src = "https://user-images.githubusercontent.com/69036517/172577395-17243e2b-1b8c-4109-a405-afec7275a636.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577273-31b4ee49-9f78-44ba-837d-fa293f417d36.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577456-dca4392f-6149-4c07-b031-f6442bc68a7f.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577369-112cd315-dc87-4f2d-8573-61416714478f.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172580845-a21aa26d-28d0-4f49-9205-2d59f04ed5a7.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172577424-2e8cd21a-803a-47da-a59b-9639ba2f2a4a.png" width = "320px">
<img src = "https://user-images.githubusercontent.com/69036517/172581269-4924a22b-3c83-4405-92bc-5301a8ee3932.png" width = "320px">
