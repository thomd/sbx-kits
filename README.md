# Docker Sandbox Kits
    
    cd ~/develop/github
    gh repo clone thomd/sbx-kits

## Secure Node

    sbx run --kit ~/develop/github/sbx-kits/node-secure/ <agent> .

or layer it onto an existing sandbox:

    sbx kit add my-sandbox /absolute/path/to/sbx-kits/node-secure/
