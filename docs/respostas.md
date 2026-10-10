### Análise da situação inicial

**1. Onde o segredo está armazenado?**

O segredo está armazenado diretamente no arquivo `.github/workflows/pipeline.yml`, no campo `MENSAGEM_SECRETA` da etapa de execução da aplicação.

**2. Quem poderia visualizar essa informação?**

Pessoas com acesso ao arquivo do repositório poderiam visualizar o valor. Dependendo das permissões e da visibilidade do repositório, isso poderia incluir colaboradores e outras pessoas que tivessem acesso ao código.

**3. Por que essa prática não é recomendada?**

Porque informações sensíveis não devem ser armazenadas diretamente em arquivos versionados. O valor pode permanecer no histórico de commits mesmo depois de ser removido do arquivo atual.

**4. O que poderia acontecer se essa informação fosse uma senha ou um token real?**

Uma pessoa não autorizada poderia utilizar a credencial para tentar acessar sistemas, bancos de dados ou serviços, causando vazamento de informações ou outras ações indevidas.

### Respostas da seção 7

**1. Qual é a diferença entre armazenar o valor diretamente no pipeline.yml e armazená-lo no GitHub Secrets?**

Quando o valor fica diretamente no YAML, ele faz parte de um arquivo versionado e pode ser visualizado por quem tem acesso ao repositório. No GitHub Secrets, o valor é armazenado separadamente, de forma protegida, e pode ser utilizado pela pipeline sem ser escrito diretamente no código. 
Documentos do GitHub

**2. Onde o valor do Secret fica configurado?**

Em Settings → Secrets and variables → Actions → Repository secrets, dentro do repositório do projeto.

**3. O valor do Secret deve ser colocado no código da aplicação?**

Não. O código deve acessar a variável de ambiente, sem precisar conhecer ou armazenar diretamente o valor sensível.

**4. Qual é a função de process.env.MENSAGEM_SECRETA?**

É acessar, no Node.js, a variável de ambiente chamada MENSAGEM_SECRETA, disponibilizada durante a execução da aplicação.

**5. Por que utilizar Secrets é importante em uma pipeline de CI/CD?**

Porque permite separar informações sensíveis dos arquivos do projeto, reduzindo o risco de exposição acidental de senhas, tokens e outras credenciais durante o desenvolvimento e a automação.

**6. Por que seria inadequado colocar uma senha real de banco de dados diretamente no arquivo YAML?**

Porque a senha poderia ficar visível no repositório e no histórico de versões para pessoas com acesso aos arquivos. Se fosse exposta, alguém poderia tentar acessar o banco de dados sem autorização. O ideal é armazená-la como Secret e disponibilizá-la somente aos passos que realmente precisam dela.