## Overview

1. Actions become plugins
1. Actions communicate via events
1. Co-dependent plugins specify peer-dependencies


## Phase 1

- docpad-plugin-run
    - actions expose
        - run
    - events expose
        - runBefore
        - runAfter
    - peerDependencies
        - docpad-plugin-generate
        - docpad-plugin-server
        - docpad-plugin-watch
- docpad-plugin-watch
    - actions expose
        - watch
    - events expose
        - watchBefore
        - watchAfter
        - watchOccured
    - dependencies
        - watchr
    - peerDependencies
        - docpad-plugin-generate
- docpad-plugin-server
    - actions expose
        - server
    - methods expose
        - getServer
        - setServer
    - events expose
        - serverBefore
        - serverExtend
        - serverAfter
    - dependencies
        - express
- docpad-plugin-generate (remains core)


## Phase 2

- docpad-plugin-generate
    - actions expose
        - watch
    - events expose
        - generateBefore
        - generateAfter
- docpad-plugin-fs
    - events listen
        - readFile
        - readDirectory
        - writeFile
- docpad-plugin-tumblr
    - events listen
        - readFile
        - readDirectory
- docpad-plugin-mongodb
    - events listen
        - readFile
        - readDirectory
        - writeFile

## Phase 3

- docpad-plugin-watch
    - actions exposed
        - watch
    - events triggered
        - watchFiles
        - watchFile
        - unwatchFile
        - unwatchFiles
    - dependencies
        - none
- docpad-plugin-fs
    - events listen
        - watchFiles
        - watchFile
        - unwatchFile
        - unwatchFiles
    - dependencies
        - watchr
- docpad-plugin-mongodb
    - events listen
        - watchFiles
        - watchFile
        - unwatchFile
        - unwatchFiles
