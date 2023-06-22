# AWS

## Modulo 3
### Infraestrutura Global e Confiabilidade

Aprendizados : 
 - [ ] Resumir os benefícios da infraestrutura global da AWS.
 - [ ] Descrever o conceito básico de Zonas de Disponibilidade.
 - [ ] Descrever os benefícios do Amazon CloudFront e dos locais de borda.
 - [ ] Comparar métodos diferentes de provisionamento de serviços AWS.

A aws precisa de alta disponibilidade ao redor do mundo para ficar altamente disponivel.

As Regiões ficam proximas aos fluxos de negocios mais precisam:
 - Paris
 - Tokio
 - São Paulo

As regioes são conectadas com uma rede de fibra optica de alta velocidade.

Uma região não se convesa com a outra ao menos que voce permita.

Qual região escolher para o negocio?
 - 1 - Conformidade: Voce precisa que os dados sejam necessariamente armazenado no Brasil? ou não importa onde será armazenado? Algumas empresas precisam que os dados sejam armazenados no Brasil ou em outra região por lei.
 - 2 - Proximidade: Quanto mais proximo a região está da sua base de clientes, mais rapido será a latência.
 - 3 - Diponibilidade dos serviços: Alguns serviços da AWS não tem em algumas regiões por motivos de demanda, hardware...
- 4 - Preço: Alguns locais do planeta tem custos maiores para operar os mesmos hardwares do que outros lugares. Exemplo: O Brasil tem taxas tributárias 50% maiores do que Oregon, portanto deixando mais caro. Mas ainda sim um serviço AWS pode rodar de uma região para outra.  

### Zonas de disponibilidade 

A AWS chama um único datacenter, ou um grupo de datacenters, de zona de disponibilidade, ou AZ.
Cada zona de disponibilidade tem redundancia  de alimentação, redes e conectividade.  

Uma pratica recomendada executar aplicativos em pelo menos 2 zonas de disponibilidade. Caso esse edificio caia, ou acontecer algo com o datacenter, o EC2 ainda estará funcionando por estar em outras zonas de disponibilidade.
  
### Pontos de presença

Edge locations executam o Amazon CloudFront.
Um local de bords é um site que Amazon CloudFront usa para armazenar cópias em cache do seu conteudo mais proximos dos seus clientes para uma entrega mais rapida.
Como funciona ?

- Origem -> Imagina que seus dados estejam no Brasil e os clientes que farão as requisicoes estão na China. Voce não precisa necessariamente mover todo o conteudo para alguma das regioes da China.

- Local de borda -> Em vez de os clientes sempre pegarem dados do Brasil, a gente pode armazenar em um cache local perto da China.

- Cliente -> Quando o cliente solicita dados vindo da região do Brasil, o Amazon CloudFront recupera os dados a partir do cache local perto da China e e entrega o arquivo ao cliente. O arquivo é entregue de forma mais rapida ao cliente pois veio de um local de borda proximo da China ao inves de vir do Brasil.

### Como provisionar recursos AWS

Na AWS tudo interage via API.

Para interagir com serviços AWS pode-se fazer via :
 - Console de Gerenciamento AWS
 - Interface de linha de comando aws (CLI)
 - SDKs (com linguagens de programação)
 - Varios outros

Existe **AWS CloudFormation** para criar ambientes inteiros de forma centralizada utilizando chamada de API da aws para gerenciar esses recursos.