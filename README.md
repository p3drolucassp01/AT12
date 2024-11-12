

## Exercícios - Primeira Aula




## Exercício 1 



**Etapas**:

1. Criação de uma nova pasta com o comando `mkdir` chamada `git-historico`.
2. Inicialização do repositório Git dentro da pasta criada com o comando:
   ```bash
   git init
   ```
3. Três arquivos foram criados usando o editor (vscode):
   - `notas.txt`: com conteúdo pertinente incluído.
   - `resumo.md`: contendo uma descrição ou resumo.
   - `tarefa.txt`: com uma breve descrição de uma tarefa ou objetivo.

4. Realizei commits separados para cada arquivo utilizando mensagens que descrevem o conteúdo adicionado ou a finalidade de cada arquivo.
5. Verificação do histórico de commits através do comando:
   ```bash
   git log
   ```

---

## Exercício 2 



**Etapas**:

1. Realizei uma alteração em `notas.txt`.
2. Adicionei e commitei a alteração.
3. Reverti a modificação para retornar ao estado anterior com o comando:
   ```bash
   git revert HEAD
   ```

---

## Exercício 3 



**Etapas**:

1. Criei uma nova branch chamada `nova-funcionalidade`:
   ```bash
   git branch nova-funcionalidade
   ```
2. Alterações foram realizadas nesta branch.
3. Integrei a branch `nova-funcionalidade` na branch principal (`main`) por meio do comando:
   ```bash
   git merge nova-funcionalidade
   ```

---



