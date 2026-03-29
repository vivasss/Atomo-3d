Aqui está a documentação estruturada em Markdown, pronta para ser utilizada em repositórios, wikis ou apresentações:

---

# Orbitais Atômicos — Visualização 3D de Densidade Quântica

## Visão Geral
Esta aplicação web interativa utiliza **Three.js** para visualizar a densidade de probabilidade quântica de orbitais atômicos (s, p, d, f). Um sistema de partículas posicionadas conforme a função de onda \(|\psi|^2\) reproduz a forma tridimensional dos orbitais, permitindo exploração livre por meio de controles de órbita.

---

## Tecnologias Utilizadas
- **Three.js (r128)** – renderização 3D, câmera, controles e sistema de partículas.
- **OrbitControls** – interação com a cena (rotação, zoom).
- **HTML5/CSS3** – interface moderna com fundo escuro e elementos translúcidos.
- **JavaScript (ES6)** – lógica de amostragem de probabilidade e gerenciamento de estado.

---

## Mecanismo de Geração das Partículas

### Definição dos orbitais
Cada tipo orbital (s, p, d, f) possui uma lista de sub‑orbitais (ex.: 1s, 2px, 3dz²). Para cada sub‑orbital são fornecidos:
- Números quânticos \(n, l, m\)
- Expressão da função de onda \(\psi\) (radial + angular)
- Descrição textual e fórmula visual

### Amostragem por rejeição
- A função de probabilidade é \(P \propto |\psi|^2 \cdot r^2 \sin\theta\) (densidade no espaço 3D).
- Primeiro, calcula-se o valor máximo de \(P\) sobre o domínio (raio máximo \(n^2 \times 3.5\)).
- Em seguida, gera-se pontos \((r, \theta, \phi)\) uniformemente dentro da esfera e aceita-se o ponto com probabilidade \(P / P_{\text{max}}\).
- O processo repete até que o número desejado de partículas seja atingido.

### Transformação para coordenadas cartesianas
Aplica-se um fator de escala visual para melhor visualização.

---

## Estrutura da Interface

| Componente | Descrição |
|------------|-----------|
| **Painel lateral esquerdo** | Botões para selecionar o tipo de orbital (s, p, d, f). Ao clicar, o orbital ativo é alterado e os sub‑orbitais são atualizados. |
| **Painel inferior central** | Botões para cada sub‑orbital (ex.: 1s, 2s, 3s). Permite alternar entre diferentes números quânticos do mesmo tipo. |
| **Painel de informações** (canto inferior direito) | Exibe nome, números quânticos, descrição e a fórmula da função de onda do orbital selecionado. |
| **Painel de ajustes** (canto direito central) | Controles deslizantes para:<br> • **Partículas** – número total de pontos (2000 a 25000)<br> • **Dinâmica** – intensidade do movimento oscilatório suave das partículas<br> • **Tamanho** – diâmetro visual de cada ponto |
| **Núcleo central** | Esfera luminosa que pulsa suavemente e muda de cor conforme o orbital ativo. |
| **Eixos de referência** | Linhas semi‑transparentes para orientação espacial. |

---

## Interação e Animação
- **OrbitControls** permite rotacionar e dar zoom com o mouse.
- **Auto‑rotação** habilitada por padrão (velocidade 0.4).
- **Transição visual** – um flash radial com a cor do orbital ocorre ao trocar de tipo ou sub‑orbital.
- **Movimento das partículas** – cada partícula oscila em torno de sua posição base com uma frequência pseudo‑aleatória, controlada pelo slider “Dinâmica”.

---

## Implementação das Funções de Onda
- **Parte radial**: polinômios de Laguerre simplificados para \(n \le 4\) e \(l \le 3\).
- **Parte angular**: harmônicos esféricos reais para os orbitais s, p, d e f, incluindo as combinações lineares que produzem as formas \(p_x, p_y, d_{xy}, d_{x^2-y^2}, f_{xyz}\), etc.
- A probabilidade é calculada como \(|\psi|^2\) multiplicada pelo elemento de volume \(r^2 \sin\theta\) para amostragem correta em coordenadas esféricas.

---

## Performance
- O número de partículas é configurável, garantindo fluidez em diferentes dispositivos.
- A geração de pontos ocorre apenas quando o orbital é alterado; depois disso, apenas as posições são atualizadas na animação.
- Uso de `BufferGeometry` e `PointsMaterial` com textura circular para otimização.

---

## Responsividade
Em telas menores que **768px**, o painel de ajustes é ocultado e a largura do painel de informações é reduzida para preservar a área de visualização.

---

## Como Utilizar
1. Abra o arquivo HTML em qualquer navegador moderno (WebGL necessário).
2. Use o mouse para rotacionar e aproximar da nuvem de pontos.
3. Clique nos botões laterais para escolher o tipo de orbital (s, p, d, f).
4. Selecione o sub‑orbital desejado no painel inferior (ex.: 2px, 3dz²).
5. Ajuste a quantidade de partículas, a intensidade do movimento e o tamanho dos pontos conforme preferir.

---

## Exemplos de Orbitais
- **s (esférico)** – distribuição simétrica, com nós radiais em 2s e 3s.
- **p (lobular)** – dois lóbulos com orientação x, y ou z.
- **d (quadrilobular)** – quatro lóbulos em configurações como dz² (com anel equatorial) e dxy.
- **f (multilobular)** – formas complexas com até oito lóbulos.

---

## Licença e Créditos
Este projeto foi desenvolvido como demonstração didática de conceitos de mecânica quântica e visualização 3D. As expressões das funções de onda são aproximações pedagógicas baseadas nas soluções da equação de Schrödinger para o átomo de hidrogênio.
Made by Josué elias Otto / Jr :)

---
