# 🧪 RAYO Labs — Ambiente de Testes

Repositório de **homologação e experimentação** do **RAYO**, aplicativo pessoal de controle financeiro utilizado por Leandro e Ray.

Aqui testamos novas funcionalidades, melhorias visuais e correções **antes** de levá-las à versão principal. O objetivo é evoluir o RAYO sem comprometer os dados, a experiência ou os recursos que já funcionam.

> [!IMPORTANT]
> **Este é um ambiente de testes, não a versão oficial.** Funcionalidades podem mudar, apresentar erros ou estar incompletas. Evite registrar dados financeiros reais neste espaço.

## 🎯 Objetivos

- Validar melhorias no computador e no celular, especialmente no iPhone.
- Testar novas funções sem interferir no RAYO principal.
- Verificar se os dados, perfis e preferências continuam preservados.
- Aprovar alterações antes de publicar em produção.

## 🚧 Funcionalidades em avaliação

| Funcionalidade | O que validar | Situação |
| --- | --- | --- |
| Botão **+** no celular | Centralização real na navegação inferior e abertura correta do menu | 🧪 Em teste |
| Foto de nota fiscal | Tirar/enviar foto, identificar os dados e conferir antes de salvar | 🧪 Em teste |
| Classificação por nota | Gastos provenientes de notas lançados como **variáveis** por padrão | 🧪 Em teste |
| Lançamentos futuros | Ganhos/gastos com data futura aparecem automaticamente como **previstos** | 🧪 Em teste |
| Mudança automática de situação | Ao chegar a data cadastrada, a situação é recalculada sem edição manual | 🧪 Em teste |
| Compatibilidade | Layout, botões e formulários no iPhone, Android e desktop | 🧪 Em teste |
| Preservação dos dados | Nenhuma atualização apaga registros ou configurações existentes | 🧪 Em teste |

**Importante:** a chegada da data não comprova que uma transação foi efetivamente paga ou recebida no banco. A classificação por data deve ser diferenciada da conciliação financeira.

## 🔒 Segurança e isolamento

**Uma URL de teste separada não significa dados separados.** Se o ambiente de testes usar o mesmo Cloudflare Worker, banco D1, chaves de armazenamento ou serviços de produção, poderá ler ou modificar dados reais.

Para testar com segurança:

1. Utilize **Worker, banco de dados e configurações próprios para testes** quando houver escrita ou sincronização.
2. Não reutilize credenciais, tokens ou chaves de produção no código público do GitHub.
3. Não publique notas fiscais reais, dados bancários, documentos pessoais ou arquivos com segredos.
4. Use dados fictícios e perfis de teste; confira que Leandro e Ray continuam com contas separadas.
5. Faça backup da versão estável antes de substituir qualquer arquivo.
6. Mantenha o RAYO principal inalterado até a conclusão e aprovação dos testes.

## 🚀 Como publicar a versão de testes no GitHub Pages

1. Crie um repositório separado, por exemplo `rayo-testes`.
2. Adicione o arquivo `index.html` da versão experimental e este `README.md` na raiz do repositório.
3. No GitHub, abra **Settings → Pages**.
4. Em **Build and deployment**, selecione **Deploy from a branch**.
5. Selecione a branch `main` e a pasta **`/(root)`**, depois salve.
6. Acesse o endereço fornecido pelo GitHub Pages após a publicação.

> [!NOTE]
> O GitHub Pages publica os arquivos do site, mas **não cria um backend de testes automaticamente**. Verifique a configuração do Worker e do banco de dados antes de testar lançamentos e sincronização.

## ✅ Checklist antes de aprovar uma atualização

- [ ] O botão **+** está centralizado em celulares de diferentes tamanhos.
- [ ] O menu **+** abre e oferece as opções esperadas.
- [ ] A câmera ou seleção de imagens funciona no iPhone.
- [ ] É possível revisar valor, estabelecimento e data extraídos da nota antes de confirmar.
- [ ] Uma nota não gera despesas duplicadas ao ser reenviada ou confirmada duas vezes.
- [ ] Um gasto de amanhã aparece como **previsto** hoje.
- [ ] Um ganho de amanhã aparece como **previsto** hoje.
- [ ] A classificação muda conforme a data atual sem precisar editar o registro.
- [ ] Uma transação prevista não afeta indevidamente o saldo disponível atual.
- [ ] Os registros e as preferências anteriores continuam acessíveis.
- [ ] Os dados de Leandro e Ray não se misturam.
- [ ] O site funciona no desktop e no celular, sem zoom inesperado nos campos.
- [ ] O ambiente de teste não escreve no banco de produção.

## 🔁 Fluxo de atualização

**Ideia → Desenvolvimento → Testes → Correção → Aprovação → Publicação no RAYO principal**

Cada mudança deve ser testada antes de migrar para a versão estável. Se apresentar algum problema, mantenha o site principal como está e corrija primeiro a cópia experimental.

## 📁 Organização sugerida

```text
rayo-testes/
├── index.html       # Versão experimental do site
├── README.md        # Objetivos e checklist de homologação
└── CHANGELOG.md     # Histórico de alterações (opcional)
```

## 📝 Registro de testes

Ao relatar um erro ou melhoria, informe:

- **Dispositivo/navegador:** exemplo: iPhone com Safari.
- **O que foi feito:** passos para reproduzir.
- **O que aconteceu:** resultado encontrado.
- **O que era esperado:** comportamento correto.
- **Print**, se ajudar (sem dados pessoais).

---

**RAYO Labs** • Um espaço para experimentar, melhorar e validar com segurança antes de atualizar o RAYO principal.
