# 🐍 Jogo da Cobra com Contribuições do GitHub!

Transforme o gráfico de contribuições do seu GitHub em um jogo de cobra! 🍏🚀

<picture> 
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/pjxsantos/snake/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/pjxsantos/snake/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/pjxsantos/snake/output/github-contribution-grid-snake.svg">
</picture> 

**O que é isso?**  
Aqui, vamos criar uma animação interativa onde a cobra "come" as células do seu gráfico de contribuições do GitHub, criando um jogo divertido com o seu histórico de commits! 🔥

## Como Funciona

1. **Crie um Repositório com seu Nome de Usuário no GitHub**
   - Exemplo: "Pjxsantos/Pjxsantos"
   - Certifique-se de tornar o repositório **público** e adicionar um arquivo `README.md`.

2. **Prepare seu Projeto com a Estrutura Necessária**
   Crie dois diretórios e o arquivo de workflow `.github/workflows/main.yml`. 
   - Exemplo de estrutura do diretório:  
     `.github/workflows/main.yml`
   - Cole o código a seguir no arquivo `main.yml` e faça o primeiro **Commit changes**.

### Código para o arquivo `main.yml`:
```yaml
name: gerar animação 🕹️🐍

on: 
  # Executa automaticamente a cada 24 horas
  schedule: 
    - cron: "0 */24 * * *"  

  # Permite execução manual
  workflow_dispatch: 

  # Executa em cada push no branch master
  push: 
    branches: 
    - master
    
jobs: 
  generate: 
    permissions:  
      contents: write 
    runs-on: ubuntu-latest 
    timeout-minutes: 5 

    steps: 
      # Gera a animação do jogo da cobra a partir do gráfico de contribuições do usuário GitHub
      - name: generate github-contribution-grid-snake.svg
        uses: pjxsantos/snake/gerar-cobrinha-svg@v5.0.2
        with: 
          github_user_name: ${{ github.repository_owner }} 
          outputs: | 
            dist/github-contribution-grid-snake.svg 
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
      # Envia o conteúdo gerado para o branch de saída
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v4.0.0
        with: 
          target_branch: output
          build_dir: dist
        env: 
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```  

3. **Atualize o README.md**

No arquivo README.md, substitua USER_NAME pelo seu nome de usuário no GitHub e o nome do repositório no lugar de USER_NAME/USER_NAME.

**Exemplo:** "Pjxsantos/Pjxsantos"

**Código:** 

``` 
<picture>

  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/USER_NAME/USER_NAME/output/github-contribution-grid-snake-dark.svg">

  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/USER_NAME/USER_NAME/output/github-contribution-grid-snake.svg">

  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/USER_NAME/USER_NAME/output/github-contribution-grid-snake.svg">

</picture> 

```  
** Finalizando o Processo: **

    Faça Commit changes novamente no seu repositório.
    Vá até a seção Actions no seu GitHub.
    Clique em "gerar animação".
    Após isso, clique em "Run workflow".

** ✨ Voilà! Sua snake estará pronta e comendo os "commit changes"! 🐍🍏 **
