## Gere um jogo de cobra a partir de um gráfico de contribuições de usuários do GitHub!

<picture> 

  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/pjxsantos/snake/output/github-contribution-grid-snake-dark.svg">

  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/pjxsantos/snake/output/github-contribution-grid-snake.svg">

  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/pjxsantos/snake/output/github-contribution-grid-snake.svg">

</picture> 
 

Extraia o gráfico de contribuição de um usuário do GitHub, faça disso um jogo de cobra, gere um caminho de cobra onde as células são comidas de maneira ordenada.

Gere uma imagem GIF ou SVG!

**Vamos ao que interessa!**

1- Crie um novo repositório com o mesmo nome de seu usuário GitHub, por exemplo, "Pjxsantos/Pjxsantos". Marque como "Público" e adicione um arquivo "README.md".

2- Na raiz do projeto, você vai ter que criar dois diretórios e um arquivo "main.yml". Por exemplo: ".github/workflows/main.yml" e vai copiar e colar no arquivo "main.yml" o código que vou disponibilizar abaixo, depois faça um "Commit changes".

**Copie o Código:** 
   
```
name: gerar animação 🕹️🐍 

on: 
  # executa automaticamente a cada 24 horas 
  schedule: 
    - cron: "0 */24 * * *"  
  
  # permite executar manualmente o trabalho a qualquer momento 
  workflow_dispatch: 
  
  # executa em cada push no branch master 
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
      # gera um jogo de cobra a partir de um gráfico de contribuições de um usuário do github  (<github_user_name>), gera uma animação SVG em <svg_out_path> 
      - name: generate github-contribution-grid-snake.svg 
        uses: pjxsantos/snake/gerar-cobrinha-svg@v5.0.2 
        with: 
          github_user_name: ${{ github.repository_owner }} 
          outputs: | 
            dist/github-contribution-grid-snake.svg 
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark 
          
          
      # envia o conteúdo de <build_dir> para um branch 
      # o conteúdo estará disponível em https://raw.githubusercontent.com/<github_user>/ <repository>/<target_branch>/<file> ou como página do github 
      - name: push github-contribution-grid-snake.svg to the output branch 
        uses: crazy-max/ghaction-github-pages@v4.0.0 
        with: 
          target_branch: output 
          build_dir: dist 
        env: 
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }} 
```  


3- Agora vamos editar o arquivo “README.md”! No arquivo “README.md”, você copia e cola o código que está disponível aqui embaixo. Onde estiver escrito “user”, você substitui pelo seu usuário, e em seguida, pelo nome do repositório.

**Exemplo:** "Pjxsantos/Pjxsantos"

**Código:** 

``` 
<picture>

  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/USER_NAME/USER_NAME/output/github-contribution-grid-snake-dark.svg">

  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/USER_NAME/USER_NAME/output/github-contribution-grid-snake.svg">

  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/USER_NAME/USER_NAME/output/github-contribution-grid-snake.svg">

</picture> 

```  
Feito isso mais uma vez  **"Commit changes"**! 

Feito isso, faça mais uma vez um “Commit changes”.

4- Por fim, você vai em “Actions”.

5- Clica em “gerar animação”.

6- Depois “Run workflow”, e pronto, você acaba de gerar uma snake comedora de “Commit changes”!

_Generated with [Platane/snk](https://github.com/Platane/snk)_
