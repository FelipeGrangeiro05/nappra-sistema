# NAPPRA — Sistema de Investigação Patrimonial CI² · MPRJ

## Visão Geral
Sistema web React interno para suporte à investigação patrimonial e recuperação de ativos do **MPRJ / CI² · NAPPRA** (Núcleo de Apoio à Persecução Patrimonial e Recuperação de Ativos).

## Stack
- **React** (JSX, hooks: useState, useMemo)
- **SheetJS (xlsx)** para exportação
- **CSS inline** — sem Tailwind, sem CSS modules
- **Google Fonts**: Plus Jakarta Sans + Instrument Serif + JetBrains Mono
- **Ambiente**: VS Code + Node.js, roda em `localhost:3000`
- **Arquivo principal**: `src/App.js` (monolítico, ~1800 linhas)

## Identidade Visual
- Bordô: `#7B1E2E` | Ouro: `#D4A017` / `#c8973a`
- Sidebar: `#1a1f2e` (escuro fixo)
- Topbar: bordô com brasão MPRJ (base64 PNG embutido)
- Fundo padrão: bege `#f5f0e8` com marca d'água MPRJ-CI²

## Estrutura do App.js
```
BRASAO          → base64 do brasão MPRJ
C               → objeto de cores (paleta global)
USUARIOS_DB     → 5 usuários de teste
CASOS           → 14 casos reais cadastrados
ILHAS_DATA      → fases de investigação por caso
PF_DATA / PJ_DATA / BENS_DATA → registros por caso
TEMAS           → 6 temas de fundo disponíveis
getFundoStyle() → aplica background conforme tema
MarcaDagua      → marca d'água animada
CaixaIlha       → cards escuros das fases (dark fixo)
GraficoGantt    → Gantt com tooltip hover
CategoriaCasos  → lista expansível na sidebar
ModalConfiguracoes → modal de configurações (tema + alertas)
TelaLogin       → tela de login institucional
RelogioRodape   → relógio por extenso em tempo real
PainelPrincipal → componente principal (~1000 linhas)
App             → root com roteamento login/painel
```

## 14 Casos Cadastrados
CASO .30, CASO QUÉOPS, CASO CASA CAIU, CASO MORRO DO MORCEGO,
CASO PRATO FEITO, CASO OBSCURITAS PECUNIAE, CASO VALE O ESCRITO,
CASO PEIXOTO, CASO BM BETS, CASO FARMÁCIAS, CASO FIGUEIRAL,
CASO BM_2, CASO FAT, CASO SAQUAREMA

## Credenciais de Teste
| Matrícula  | Senha       | Nível          |
|------------|-------------|----------------|
| admin      | nappra2025  | Administrador  |
| super      | super2025   | Super Admin    |
| mineral1   | min2025     | Minerador      |
| analista   | ana2025     | Analista       |
| viewer     | view2025    | Visualizador   |

## Funcionalidades Implementadas ✅
- Login com autenticação por matrícula/senha
- Topbar 2 níveis (sub-barra preta + barra bordô com brasão)
- Dropdown de perfil com Configurações e Sair
- Sidebar com SVG icons, grupos "Registros" / "Gestão", lista de casos por categoria
- 6 temas de fundo selecionáveis por usuário (salvo em localStorage)
- Modal de Configurações: aba Tema + aba Alertas (parâmetro global de dias)
- Badge de alertas clicável na topbar → popup com lista de casos sem movimentação
- Status bar horizontal (Ativos / Concluídos / Aguardando) com hover e filtro
- 4 ilhas da Metodologia NAPPRA (dark, gradiente por fase)
- Controle Operacional de Casos (tabela 7 colunas, filtros, scroll)
- Status badges pílula com dot pulsante (ATIVO) / SVG check (CONCLUÍDO)
- Dias de Trabalho: concluídos em verde, ativos piscando em amarelo
- Valor Patrimonial calculado de BENS_DATA por caso
- Gráfico de Gantt com tooltip flutuante ao hover nas barras
- Dashboard cards (6 cards, ícone gradiente, border-left colorido)
- Módulos PF / PJ / Bens (tabelas por caso)
- Exportar .xlsx (4 abas: Casos, PF, PJ, Bens)
- Busca global (CPF, CNPJ, nome, caso) com dropdown em tempo real
- Relógio por extenso no rodapé fixo
- Scrollbar customizado dourado 4px

## Próximas Funcionalidades 🔲
1. **Tela individual de cada caso** — ao clicar no nome abre tela dedicada
2. **Cadastro real de PF/PJ/Bens** dentro de cada caso
3. **Módulo de Relatórios** (Word/PDF)
4. **Módulo de Auditoria** completo
5. **Gestão de usuários** pelo Super Admin
6. **Dark mode correto** via CSS variables (sessão dedicada futura)

## Padrões e Regras Importantes
- **NUNCA** usar regex `[\s\S]*?` para substituições em JSX
- **SideBtn** e **SideCat** devem ser `const` DENTRO do `PainelPrincipal`
- `useEffect` deve ser importado explicitamente se usado
- `useState` não pode ser chamado dentro de IIFE/callbacks
- localStorage keyed por matrícula: `"nappra_tema_"+usuario.matricula`
- Alerta global: `"nappra_diasAlerta"` (sem matrícula)
- Chrome auto-translate corrompe labels → usar `translate="no"`
- Temas disponíveis: bege-watermark, bege-premium, cinza-suave, micro-grade, radial-elegante, dark-premium, branco-puro, azul-institucional

## Localização dos Arquivos
- Projeto local: `C:\Users\ESMERALDA\nappra-sistema\`
- Arquivo principal: `src/App.js`
- Rodar: `npm start` na pasta do projeto
