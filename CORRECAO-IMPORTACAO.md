CORREÇÃO DO ODONTOMESH — IMPORTAÇÃO STL/PLY

Causa provável:
A interface usa módulos JavaScript ES importados por caminho relativo em uma aplicação Electron carregada com file://.
Em algumas configurações do Electron, esses módulos não são carregados corretamente; por isso o botão não responde.

Correção:
- Empacota renderer.js e os módulos Three.js em um único arquivo renderer.bundle.js usando esbuild.
- index.html carrega o bundle em vez de um módulo externo.
- O fluxo do GitHub Actions gera o bundle antes de compilar a aplicação Windows.

Como aplicar:
1. Extraia este ZIP.
2. Copie o conteúdo para a pasta local OdontoMesh do GitHub Desktop, substituindo os arquivos de mesmo nome.
3. No GitHub Desktop, faça Commit e depois Push origin.
4. Abra Actions no GitHub e aguarde a nova compilação verde.
5. Baixe o novo artefato e execute o aplicativo atualizado.

Observação: esta correção trata o problema provável de carregamento do JavaScript. A confirmação final é abrir a versão recompilada e testar a importação de arquivos STL e PLY reais.
