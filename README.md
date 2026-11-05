# Lab de Segurança de APIs | Professor Rodrigo

Laboratório interativo, responsivo e independente de instituições ou turmas. Preparado para publicação no GitHub Pages.

## Páginas

- `index.html`: apresentação visual dos conceitos e do cenário da biblioteca.
- `demonstracao.html`: simulação de papéis e permissões, login fictício, emissão e verificação de JWT HS256 com Web Crypto, análise do token, console de API com operações GET/POST/PUT/DELETE e status HTTP.
- `atividade.html`: desafio de 40 minutos, construção de política, reflexão sobre JWT e exceções, cenários HTTP, quiz de oito perguntas com autocorreção e relatório em PDF/TXT.
- `styles.css`, `app.js`, `favicon.svg`: estilos, funcionamento e ícone.
- `backend_opcional/`: exemplo separado de API real FastAPI com JWT e Swagger integrado.

## Publicação no GitHub Pages

1. Crie um repositório, por exemplo `lab-seguranca-apis`.
2. Envie os arquivos `index.html`, `demonstracao.html`, `atividade.html`, `styles.css`, `app.js` e `favicon.svg` para a raiz do repositório. O diretório `backend_opcional` pode ficar no repositório como material adicional, mas **não é executado** pelo GitHub Pages.
3. Em **Settings > Pages**, em **Build and deployment**, escolha **Deploy from a branch**, branch `main` e pasta `/(root)`.
4. Abra o endereço fornecido pelo GitHub Pages.
5. Oriente os alunos a usar apenas contas e dados fictícios.

A página **não possui contas reais, não recebe arquivos ou respostas e não envia dados a um servidor**. Respostas da atividade são guardadas no `localStorage` do navegador. A sessão JWT da demonstração existe apenas em memória e é perdida quando a página é recarregada.

## Segurança: distinção essencial

Este site é estático. Embora utilize a Web Crypto API para criar/verificar uma assinatura HMAC de demonstração, **não existe backend confiável**: nenhuma senha, chave ou regra dentro de código JavaScript publicado deve ser considerada segredo ou segurança real.

Um JWT assinado (JWS) não é necessariamente criptografado. O Payload pode ser decodificado. Em APIs reais, credenciais devem ser verificadas no servidor, senhas armazenadas com hashes apropriados, segredos protegidos fora do cliente e cada endpoint deve validar identidade e permissão.

Fontes de referência:
- FastAPI, tutorial oficial: https://fastapi.tiangolo.com/pt/tutorial/security/oauth2-jwt/
- OWASP REST Security Cheat Sheet: https://cheatsheetseries.owasp.org/cheatsheets/REST_Security_Cheat_Sheet.html

## Teste rápido

Abra `index.html` no navegador, clique em Laboratório e escolha uma conta de demonstração:

- `leitor` / `leitor123`
- `funcionario` / `livros123`
- `admin` / `admin123`

Teste `GET /livros` sem token, `POST /livros` sem login (401), `POST /livros` com funcionário (201), `DELETE /livros/1` com funcionário (403) e com administrador (204). Faça logout e experimente token alterado ou expirado.

## API real opcional

O exemplo FastAPI, que **não roda no GitHub Pages**, permite apresentar um servidor de desenvolvimento com documentação `/docs` em ambiente Python. Veja `backend_opcional/README.md`.
