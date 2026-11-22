# Rota a Rota

Aplicação web enxuta para pesquisar endereços, visualizar trajetos em um mapa interativo e consultar a distância e o tempo estimado entre dois locais.

O projeto surgiu durante uma busca por emprego. Ao avaliar oportunidades em diferentes bairros e cidades, era necessário verificar rapidamente a distância entre a residência e o possível local de trabalho. Embora existam diversas plataformas de mapas, a proposta foi criar uma experiência mais direta, com poucos elementos visuais e somente os recursos necessários para essa consulta.

## Demonstração

[Acessar o Rota a Rota](https://jkkbr.github.io/rotaarota/)

## Objetivo

Permitir que o usuário informe uma origem e um destino, visualize o trajeto no mapa e consulte rapidamente:

- Distância estimada em quilômetros;
- Tempo estimado em minutos;
- Localização atual, quando autorizada;
- Histórico das pesquisas recentes.

O foco do projeto é a simplicidade. A aplicação não tenta reproduzir todos os recursos de uma plataforma profissional de mapas.

## Contexto do projeto

Durante a procura por oportunidades de trabalho, a localização da empresa também precisava ser considerada antes de uma candidatura.

A aplicação foi criada para responder perguntas como:

- Onde fica a empresa?
- Qual é a distância aproximada até minha residência?
- Quanto tempo o trajeto pode levar?
- A localização parece viável para o deslocamento diário?
- Quais endereços já foram pesquisados?

## Funcionalidades

- Campo de endereço de origem;
- Campo de endereço de destino;
- Uso opcional da localização atual;
- Conversão de endereços em coordenadas;
- Exibição da rota em mapa interativo;
- Cálculo da distância estimada;
- Cálculo do tempo estimado;
- Marcador da localização atual;
- Histórico das últimas consultas;
- Armazenamento local do histórico;
- Interface com poucos elementos;
- Layout dividido entre painel e mapa.

## Fluxo de utilização

```text
Informar a origem
        ↓
Informar o destino
        ↓
Localizar os endereços
        ↓
Calcular o trajeto
        ↓
Visualizar a rota no mapa
        ↓
Consultar distância e tempo
        ↓
Salvar a consulta no histórico
```

## Como funciona

### 1. Busca de endereços

Os endereços informados são enviados ao serviço de geocodificação Nominatim. A resposta contém as coordenadas geográficas utilizadas para localizar cada ponto no mapa.

Se um endereço não for encontrado, a aplicação interrompe o cálculo e apresenta uma mensagem ao usuário.

### 2. Localização atual

Quando o usuário autoriza o acesso à localização, a aplicação:

1. Obtém a latitude e a longitude do dispositivo;
2. Centraliza o mapa na posição atual;
3. Adiciona um marcador;
4. Realiza a busca reversa do endereço;
5. Preenche automaticamente o campo de origem.

Caso a permissão não seja concedida, a origem pode ser informada manualmente.

### 3. Cálculo da rota

Depois de localizar a origem e o destino, a aplicação utiliza o Leaflet Routing Machine para criar o trajeto entre os dois pontos.

O resultado apresenta:

- Desenho da rota no mapa;
- Distância aproximada em quilômetros;
- Tempo aproximado em minutos.

### 4. Histórico local

As consultas recentes são armazenadas no `localStorage` do navegador.

O histórico mantém até dez pesquisas, apresentadas da mais recente para a mais antiga. Cada item registra o texto usado como origem e destino.

## Tecnologias utilizadas

- HTML5;
- CSS3;
- JavaScript;
- Leaflet;
- Leaflet Routing Machine;
- OpenStreetMap;
- Nominatim;
- Geolocation API;
- `localStorage`;
- GitHub Pages.

## Estrutura do projeto

```text
rotaarota/
├── index.html
├── style.css
├── script.js
└── README.md
```

## Executar localmente

O projeto não exige instalação de dependências ou processo de build.

1. Clone o repositório:

```bash
git clone https://github.com/JKKBR/rotaarota.git
```

2. Entre na pasta:

```bash
cd rotaarota
```

3. Abra o arquivo `index.html` no navegador.

Para evitar restrições do navegador relacionadas à localização ou às requisições externas, também é possível utilizar um servidor local simples.

Com Python:

```bash
python3 -m http.server 8000
```

Depois, acesse:

```text
http://localhost:8000
```

## Serviços externos

A aplicação depende de serviços externos para mapa, geocodificação e cálculo de rotas:

- OpenStreetMap para os dados do mapa;
- Nominatim para pesquisa e conversão de endereços;
- Leaflet para a interface geográfica;
- Leaflet Routing Machine para o trajeto.

O funcionamento pode ser afetado por indisponibilidade, limites ou alterações nesses serviços.

## Privacidade

- A localização atual somente é solicitada quando o usuário escolhe utilizar esse recurso;
- A permissão é controlada pelo navegador;
- O histórico é armazenado localmente no dispositivo;
- A aplicação não possui conta de usuário;
- A aplicação não sincroniza pesquisas entre dispositivos;
- A limpeza dos dados do navegador pode apagar o histórico.

## Limitações atuais

- Não apresenta condições de trânsito em tempo real;
- Não compara diferentes meios de transporte;
- Não calcula custos de deslocamento;
- Não apresenta tarifas de transporte público;
- Não organiza as rotas por vaga ou empresa;
- A estimativa de tempo pode não refletir as condições reais;
- Alguns endereços podem apresentar resultados imprecisos;
- O histórico fica limitado ao navegador utilizado;
- Não possui autenticação;
- Não sincroniza dados entre dispositivos.

## Próximas melhorias

- Permitir salvar o nome da empresa e da vaga;
- Adicionar observações às rotas;
- Criar uma lista de oportunidades pesquisadas;
- Organizar oportunidades por distância;
- Adicionar rotas favoritas;
- Permitir exclusão individual do histórico;
- Comparar diferentes trajetos;
- Calcular uma estimativa de custo de deslocamento;
- Adicionar filtro por distância máxima;
- Exportar a lista de oportunidades;
- Melhorar a experiência em dispositivos móveis;
- Adicionar estados de carregamento;
- Melhorar o tratamento de erros;
- Adicionar testes automatizados.

## Desenvolvimento assistido por IA

A inteligência artificial foi utilizada como apoio na estruturação do HTML, CSS e JavaScript, na integração inicial das bibliotecas e na investigação de problemas.

A definição do objetivo, a seleção das funcionalidades, os testes das rotas e a validação da experiência permaneceram sob revisão humana.

## Status

Protótipo funcional e disponível para demonstração.

A aplicação permite pesquisar endereços, utilizar a localização atual, visualizar uma rota, consultar distância e tempo estimado e manter um histórico local.

## Autor

**Fabio Santos**

- [Portfólio](https://ffssportfolio.vercel.app/)
- [GitHub](https://github.com/JKKBR)
- [LinkedIn](https://linkedin.com/in/fabiofss)

## Aviso

As rotas, distâncias e tempos apresentados são estimativas. O projeto possui finalidade pessoal, educacional e demonstrativa e não substitui a consulta de condições reais de trânsito, transporte público ou segurança do trajeto.
