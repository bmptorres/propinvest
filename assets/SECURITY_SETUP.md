# PropInvest - Ativacao das correcoes de seguranca

## 1. Publicar ficheiros no GitHub

Publica estes ficheiros principais da pasta da app:

- `index.html`
- `sw.js`
- `manifest.webmanifest`
- `firestore.rules`
- `propinvest-invite-appsscript-Code.gs`
- pasta `assets/`

Nao publiques ficheiros `*.codex_backup*`. Foram movidos para uma pasta local fora da app.

## 2. Firebase Authentication

No Firebase Console:

1. Vai a Authentication -> Sign-in method.
2. Mantem Email/Password ativo.
3. Mantem Google ativo apenas se quiseres permitir login Google.
4. Usa sempre emails reais dos investidores.

A app agora exige email confirmado. Se um utilizador ainda nao confirmou o email, a app nao carrega projetos.

## 3. Firestore Rules

No Firebase Console:

1. Vai a Firestore Database -> Rules.
2. Abre o ficheiro `firestore.rules` desta pasta.
3. Copia todo o conteudo.
4. Cola no editor de regras do Firebase.
5. Clica Publish.

Estas regras bloqueiam acesso anonimo, exigem `email_verified`, fecham `shared_reports` e limitam investidores aos projetos onde o email deles esta associado.

## 4. Google Apps Script dos convites

No Apps Script:

1. Abre o projeto do script de convites.
2. Substitui o conteudo pelo ficheiro `propinvest-invite-appsscript-Code.gs` desta pasta.
3. Clica Guardar.
4. Vai a Deploy -> Manage deployments.
5. Edita o deployment atual ou cria uma nova versao.
6. Em Execute as, usa `Me`.
7. Em Who has access, usa a opcao mais restrita disponivel.
8. Confirma que o URL final continua igual ao que esta no `index.html`.

O script agora valida email, tamanho da mensagem e link permitido antes de enviar.

## 5. Teste rapido

1. Abre a app pelo link GitHub Pages, nao por `file:///`.
2. Entra como admin.
3. Confirma o email da conta admin se a app pedir.
4. Cria ou abre um projeto.
5. Adiciona um investidor com email em minusculas.
6. Clica no botao `@` do investidor e envia o convite.
7. Abre o convite como investidor, cria password e confirma o email.
8. Confirma que o investidor so ve os projetos associados e nao consegue criar, editar, apagar ou usar IA.