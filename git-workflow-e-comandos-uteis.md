# 1. Convenções de Commit (Conventional Commits)

A convenção de commit é um padrão que torna o histórico do código legível, rastreável e profissional. A estrutura básica é:

```
<tipo> [escopo opcional]: <descrição concisa>
```



## Tipos Mais Comuns
|Tipo|Onde Usar|Exemplo|
|:---|:---|:---|
|**`feat`**	|Adição de um novo recurso para o usuário ou aplicação.|`feat: adicionando endpoint para relatorio financeiro`|
|**`fix`**|Correção de um bug.|`fix: corrigindo erro de arredondamento em calculo de margem`|
|**`docs`**|Mudanças que afetam apenas a documentação (READMEs, anotações de estudo).|`docs: atualizando link no README apos renomeacao de arquivo`|
|**`refactor`**|Refatoração de código que não adiciona funcionalidade nem corrige bug (ex: mudança de nomes de variáveis, reorganização).|`refactor: reorganizando funcoes de ETL em novo modulo`|
|**`style`**|Mudanças que não afetam a lógica do código (formatação, ponto e vírgula, espaços).|`style: corrigindo indentacao do arquivo principal`|
|**`chore`**|Tarefas de rotina, manutenção ou mudanças no build (não ligadas diretamente à lógica de negócio).|`chore: atualizando versao do pacote dbt no yml`

# 2. Fluxo de Trabalho Versionado e Colaborativo (Git Flow Simplificado)

Em um ambiente colaborativo, você nunca trabalha diretamente no branch principal (main). O fluxo ideal é:

1. **Iniciar o rastreamente do repositório** Etapa necessária apenas em novos projetos.
```
git init
```

2. **Criar uma nova branch:** Para isolar seu trabalho.
```
git checkout -b minha-nova-feature
```
3. **Desenvolver e enviar para preparação** Move as alterações da pasta de trabalho (working directory) para a staging area (área de preparação).
```
git add .
```
4. **Commitar:** Cria o registro histórico do seu trabalho local.
```
git commit -m "feat: adicionando tela de login"
```

5. **Conectar o Repositório Remoto** (Apenas na Primeira Vez): Associa o apelido origin à URL do seu projeto no GitHub.
```
git remote add origin <URL_DO_REPOSITÓRIO_GITHUB>
```

6. **Sincronizar** (Pull): Atualiza sua branch com as últimas mudanças do main remoto, caso outra pessoa tenha comitado. (Idealmente feito antes de enviar).
```
git pull origin main
```
7. **Enviar** (Push): Publica o trabalho no GitHub e define o rastreamento (-u)..

```
git push -u origin minha-nova-feature
```
8. **Abrir PR:** Criar um Pull Request (PR) no GitHub para que o código seja revisado e, se aprovado, mesclado ao `main`.

## Comandos de Branches
|Objetivo|Comando|
|:---|:---|
|Listar branches (local e remota)|`git branch -a`|
|Criar e Mudar para uma nova branch|`git checkout -b <nome-branch>`|
|Voltar para o main|`git checkout main`|
|Deletar uma branch local|`git branch -d <nome-branch>`|
|Deletar uma branch remota|`git push origin --delete <nome-branch>`|

<br>
<br>

# 3. Comandos Essenciais para VS Code (PowerShell)

Para garantir que o ambiente de desenvolvimento com Python e Git funcione perfeitamente no terminal PowerShell do VS Code:

### 🐍 Ambiente Virtual (VENV)
O ambiente virtual isola dependências do projeto:
|Objetivo|Comando|
|:---|:---|
|Criar venv (padrão)|`python -m venv venv`|
|Ativar venv (Windows/PS)|`.\venv\Scripts\Activate.ps1`|

### 💻 Ferramentas de Terminal (Git Status)
Estes comandos configuram o PowerShell para visualizar o status do Git e permitir a execução de scripts:

|Objetivo|Comando|
|:---|:---|
|Permitir execução temporária de scripts (Necessário para venvs e posh-git)|`Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`|
|Carregar posh-git (Ativa o status visual do Git na linha de comando)|`Import-Module posh-git`|