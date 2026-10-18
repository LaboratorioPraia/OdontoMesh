# OdontoMesh Unifier — compilação Windows sem Python

O projeto usa Electron + Three.js. A compilação é feita em um runner Windows do GitHub Actions, não requer Python.

## Gerar o executável via GitHub Actions
1. Crie um repositório privado no GitHub e envie os arquivos deste projeto.
2. A workflow `.github/workflows/build-windows.yml` executará automaticamente ao enviar para `main` ou quando iniciada manualmente.
3. Na aba **Actions**, abra a execução concluída e baixe o artefato `OdontoMeshUnifier-Windows-x64`.
4. Extraia o ZIP e execute `OdontoMesh Unifier.exe` dentro da pasta `win-unpacked`.

O build usa o alvo `dir` para produzir uma pasta portátil com o executável e os arquivos de runtime. Distribua a pasta inteira, não apenas o `.exe`.

## Teste local de desenvolvimento (opcional)
Requer Node.js 22, não Python:
- `npm install`
- `npm start`
- `npm run build:win`

## Notas de geometria
- A importação não translada nem escala os vértices.
- A exportação reúne as malhas visíveis em um STL binário.
- STL não preserva cor/material; PLY colorido é convertido para geometria sem cor na exportação STL.
- A aplicação não faz união booleana, reparação de malha ou garantia de volume fechado.
