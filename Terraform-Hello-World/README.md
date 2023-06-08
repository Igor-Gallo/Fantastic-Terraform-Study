# 🌐 Terraform Tutorial

Este tutorial irá guiá-lo através da instalação e configuração do Terraform, um cliente Git, e como usar o Terraform para gerenciar recursos na cloud.

## 📝 Índice

1. [Introdução](## 🌟 introdução)

2. [Pré-requisitos](## 🎯 Pré-requisitos)

   - [Instalação do Cliente Git](instalação-do-cliente-git)

   - [Instalação do Cliente Terraform](instalação-do-cliente-terraform)

3. [Clonagem do Repositório do GitHub](clonagem-do-repositório-do-github)

4. [Configurando as Credenciais de Acesso ao Provedor de Cloud](#-configurando-as-credenciais-de-acesso-ao-provedor-de-cloud)

5. [Planejando e Aplicando o Código Terraform na Cloud](#-planejando-e-aplicando-o-código-terraform-na-cloud)

6. [Limpeza dos Recursos Criados pelo Código Terraform na Cloud](#-limpeza-dos-recursos-criados-pelo-código-terraform-na-cloud)


## 🌟 introdução

O [Terraform](https://www.terraform.io/) é uma ferramenta para construir, alterar e controlar a infraestrutura de forma segura e eficiente. O Terraform pode gerenciar provedores de serviços existentes e populares como OpenStack, Azure, AWS, Digital Ocean, entre outras, bem como soluções internas personalizadas.

Os arquivos de configuração do Terraform descrevem os componentes necessários para executar um único aplicativo ou todo o *datacenter*, gerando um plano de execução que descreve o que será feito para alcançar o estado desejado e, em seguida, executá-lo para construir a infraestrutura descrita. À medida que a configuração muda, o Terraform é capaz de determinar o que mudou e criar planos de execução incrementais que podem ser aplicados.

A infraestrutura que o Terraform pode gerenciar inclui componentes de baixo nível, como instâncias de computação, armazenamento e redes, bem como componentes de alto nível, como entradas DNS, recursos SaaS, etc.



## 🎯 Pré-requisitos


### 💻 Instalação do Cliente Git

1. Baixar e configurar o Git client conforme instruções em [https://git-scm.com/downloads](https://git-scm.com/downloads).

2. Testar a instalação, abrindo o terminal de comando e digitando *git* como no exemplo abaixo.

    ```
    $ git
    usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
               [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
               [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]      
               [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
               [--super-prefix=<path>] [--config-env=<name>=<envvar>]
               <command> [<args>]

    These are common Git commands used in various situations:

    start a working area (see also: git help tutorial)
       clone             Clone a repository into a new directory
       init              Create an empty Git repository or reinitialize an existing one 

    work on the current change (see also: git help everyday)
       add               Add file contents to the index
       mv                Move or rename a file, a directory, or a symlink
       restore           Restore working tree files
       rm                Remove files from the working tree and from the index
       sparse-checkout   Initialize and modify the sparse-checkout

    examine the history and state (see also: git help revisions)
       bisect            Use binary search to find the commit that introduced a bug     
       diff              Show changes between commits, commit and working tree, etc     
       grep              Print lines matching a pattern
       log               Show commit logs
       show              Show various types of objects
       status            Show the working tree status

    grow, mark and tweak your common history
       branch            List, create, or delete branches
       commit            Record changes to the repository
       merge             Join two or more development histories together
       rebase            Reapply commits on top of another base tip
       reset             Reset current HEAD to the specified state
       switch            Switch branches
       tag               Create, list, delete or verify a tag object signed with GPG    

    collaborate (see also: git help workflows)
       fetch             Download objects and refs from another repository
       pull              Fetch from and integrate with another repository or a local branch
       push              Update remote refs along with associated objects

    'git help -a' and 'git help -g' list available subcommands and some
    concept guides. See 'git help <command>' or 'git help <concept>'
    to read about a specific subcommand or concept.
    See 'git help git' for an overview of the system.
    ```



### 🚀 Instalação do Cliente Terraform

1. Fazer o *download* do Terraform em [https://www.terraform.io/downloads](https://www.terraform.io/downloads).
    
2. Descompactar o arquivo baixado no diretório *C:\Windows\System32*.
   
3. Testar a instalação, abrindo o terminal de comando e digitando *terraform -h* como no exemplo abaixo.

    ```
    $ terraform -h
    Usage: terraform [global options] <subcommand> [args]

    The available commands for execution are listed below.
    The primary workflow commands are given first, followed by
    less common or more advanced commands.

    Main commands:
      init          Prepare your working directory for other commands
      validate      Check whether the configuration is valid
      plan          Show changes required by the current configuration
      apply         Create or update infrastructure
      destroy       Destroy previously-created infrastructure

    All other commands:
      console       Try Terraform expressions at an interactive command prompt
      fmt           Reformat your configuration in the standard style
      force-unlock  Release a stuck lock on the current workspace
      get           Install or upgrade remote Terraform modules
      graph         Generate a Graphviz graph of the steps in an operation
      import        Associate existing infrastructure with a Terraform resource
      login         Obtain and save credentials for a remote host
      logout        Remove locally-stored credentials for a remote host
      output        Show output values from your root module
      providers     Show the providers required for this configuration
      refresh       Update the state to match remote systems
      show          Show the current state or a saved plan
      state         Advanced state management
      taint         Mark a resource instance as not fully functional
      test          Experimental support for module integration testing
      untaint       Remove the 'tainted' state from a resource instance
      version       Show the current Terraform version
      workspace     Workspace management

    Global options (use these before the subcommand, if any):
      -chdir=DIR    Switch to a different working directory before executing the
                    given subcommand.
      -help         Show this help output, or the help for a specified subcommand.
      -version      An alias for the "version" subcommand.
    ```



## 📦 Como clonar um Repositório do GitHub

1. Clonar um repositório de exemplo : https://github.com/Igor-Gallo/Fantastic-Terraform-Study

   - Pelo Visual Studio Code:

      1. 
         ![Clone Repository](/Terraform-Hello-World/images/clone-repository.png)

   - Pelo terminal:
    ```
    $ git clone [https://github.com/Igor-Gallo/Fantastic-Terraform-Study](https://github.com/Igor-Gallo/Fantastic-Terraform-Study)
    Cloning into 'Fantastic-Terraform-Study'...
    remote: Enumerating objects: 10, done.
    remote: Counting objects: 100% (10/10), done.
    remote: Compressing objects: 100% (10/10), done.
    remote: Total 3716 (delta 4), reused 0 (delta 0), pack-reused 3706
    Receiving objects: 100% (3716/3716), 44.63 MiB | 3.88 MiB/s, done.
    Resolving deltas: 100% (1862/1862), done.
    Checking connectivity... done.
    $
    ```



## 🔐 Configurando as Credenciais de Acesso ao Provedor de Cloud

   1. Abrir a sua conta AWS.
   
   // Dê Preferência em fazer isto em uma conta que não seja root. Pois a conta root é usada geralmente somente para criação de usuários e para autenticar MFA nela, então você não irá querer ter uma possível brecha de segurança com essas credenciais que podem possívelmente ficar expostas.

   2. Entrar no IAM

      2.1 - Acessar "minhas credenciais de segurança" na aba Links Rápidos.

         ![Acesso ás credenciais](/Terraform-Hello-World/images/acesso-de-credenciais.png)

      2.2 - Realizar a criação da Access & Secret keys. Lembre -se de anotar estas credenciais em algum lugar, pois depois não terá mais como consulta-lás.

         ![Criação das credenciais](/Terraform-Hello-World/images/criacao-de-credenciais.png)

      2.3 - copiar essas variaveis com este formato no terminal do Visual Code:

   - No terminal:

   ```
   $Env:AWS_ACCESS_KEY_ID="PUT_HERE_ACCESS_KEY"
   $Env:AWS_SECRET_ACCESS_KEY="PUT_HERE_SECRET_KEY"
   $Env:AWS_DEFAULT_REGION="us-west-2"
   ```
   

## 🌐 Planejando e Aplicando o Código Terraform na Cloud


1. Inicializar o Terraform com o correspondente *provider*, seja AWS, Azure ou outro provedor, neste exemplo é a AWS:

    ```
    $ terraform init

    Initializing the backend...

    Initializing provider plugins...
    - Finding hashicorp/aws versions matching "~> 3.27"...
    - Installing hashicorp/aws v3.58.0...
    - Installed hashicorp/aws v3.58.0 (signed by HashiCorp)

    Terraform has created a lock file .terraform.lock.hcl to record the provider
    selections it made above. Include this file in your version control repository
    so that Terraform can guarantee to make the same selections by default when
    you run "terraform init" in the future.

    Terraform has been successfully initialized!

    You may now begin working with Terraform. Try running "terraform plan" to see
    any changes that are required for your infrastructure. All Terraform commands
    should now work.

    If you ever set or change modules or backend configuration for Terraform,
    rerun this command to reinitialize your working directory. If you forget, other
    commands will detect it and remind you to do so if necessary.
    ```


2. Validar o template:

    ```
    $ terraform validate
    Success! The configuration is valid.
    ```

3. Planejar a execução do código Terraform. Executar *terraform plan*.

    ```
    $ terraform plan

    Terraform used the selected providers to generate the following execution plan. Resource actions are
    indicated with the following symbols:
      + create

    Terraform will perform the following actions:

      # aws_vpc.Hello_VPC will be created
      + resource "aws_vpc" "Hello_VPC" {
          + arn                                  = (known after apply)
          + cidr_block                           = "10.0.0.0/16"
          + default_network_acl_id               = (known after apply)
          + default_route_table_id               = (known after apply)
          + default_security_group_id            = (known after apply)
          + dhcp_options_id                      = (known after apply)
          + enable_classiclink                   = (known after apply)
          + enable_classiclink_dns_support       = (known after apply)
          + ipv6_cidr_block_network_border_group = (known after apply)
          + main_route_table_id                  = (known after apply)
          + owner_id                             = (known after apply)
          + tags                                 = {
              + "Name" = "Hello VPC"
            }
          + tags_all                             = {
              + "Name" = "Hello VPC"
            }
        }

   Plan: 1 to add, 0 to change, 0 to destroy.

   ────────────────────────────────────────────────────────────────────────────────────────────────────────── 

   Note: You didn't use the -out option to save this plan, so Terraform can't guarantee to take exactly these 
   actions if you run "terraform apply" now.    
   ```

4. Aplicar a execução do código Terraform. Executar *terraform apply* para criar os recursos.

5. Validar a criação dos recursos pela AWS Console.



## 🧹 Limpeza dos Recursos Criados pelo Código Terraform na Cloud

1. Destruir os recursos criados na conta AWS.

   ```
   $ terraform destroy
   aws_vpc.Hello_VPC: Refreshing state... [id=vpc-05c18fa79e3cf13bb]

   Terraform used the selected providers to generate the following execution plan. Resource actions are
   indicated with the following symbols:
      - destroy

   Terraform will perform the following actions:

      # aws_vpc.Hello_VPC will be destroyed
      - resource "aws_vpc" "Hello_VPC" {
          - arn                              = "arn:aws:ec2:us-east-1:095383030489:vpc/vpc-05c18fa79e3cf13bb" -> null
          - assign_generated_ipv6_cidr_block = false -> null
          - cidr_block                       = "10.0.0.0/16" -> null
          - default_network_acl_id           = "acl-0c478b15ea71a2a45" -> null
          - default_route_table_id           = "rtb-0101d9b5c99bddf5a" -> null
          - default_security_group_id        = "sg-01748e63b4ce43011" -> null
          - dhcp_options_id                  = "dopt-039bff76f83af6215" -> null
          - enable_classiclink               = false -> null
          - enable_classiclink_dns_support   = false -> null
          - enable_dns_hostnames             = true -> null
          - enable_dns_support               = true -> null
          - id                               = "vpc-05c18fa79e3cf13bb" -> null
          - instance_tenancy                 = "default" -> null
          - ipv6_netmask_length              = 0 -> null
          - main_route_table_id              = "rtb-0101d9b5c99bddf5a" -> null
          - owner_id                         = "095383030489" -> null
          - tags                             = {
              - "Name" = "Hello VPC"
            } -> null
          - tags_all                         = {
              - "Name" = "Hello VPC"
            } -> null
        }

    Plan: 0 to add, 0 to change, 1 to destroy.

    Do you really want to destroy all resources?
      Terraform will destroy all your managed infrastructure, as shown above.
      There is no undo. Only 'yes' will be accepted to confirm.

      Enter a value: yes
   
   aws_vpc.Hello_VPC: Destroying... [id=vpc-05c18fa79e3cf13bb]
   aws_vpc.Hello_VPC: Destruction complete after 1s

   Destroy complete! Resources: 7 destroyed.
   ```

   
