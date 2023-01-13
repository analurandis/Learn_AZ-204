## Serviço de Aplicativo do Azure
Serviço com base em HTTP para hospedagem de aplicativos Web, APIs REST back-ends móveis.
Ambientes Windows ou Linux

- **Dimensionamento automático integrado**
Capacidades de escalar/reduzir verticalmente ou escalar/reduzir horizontalmente integrado.

- **Integração e implantações contínuas**
Sincronização automatica de codigo para Azure Devops, GitHub, Bitbucket e FTP.

- **Slots de implantação**
São aplicativos dinâmicos que possuem seus próprios nomes de hosts. Para as camadas Standard, Premium ou Isolado, slots de desenvolvimento ou produção.

#### Planos Serviço de Aplicativo do Azure
Define um conjunto de recursos de computação para um aplicativo Web ser executado, podendo ter um ou mais, e até mesmo um Functions
É unidade de escala dos aplicativos 5 instancias, todos os aplicativos estaram nas 5 instancias 
- **Definições**
    - Região (Oeste dos EUA, Leste dos EUA, etc.)
    - Número de instâncias de VM
    - Tamanho de instâncias de máquina virtual (pequeno, médio, grande)
    - Tipo de preço (Gratuito, Compartilhado, Básico, Standard, Premium, PremiumV2, PremiumV3, Isolado)

- **Preço**
    - *Computação compartilhada* -> Clientes compartilham o pool de recursos, não pode ser escalado horizontalmente
    - *Computação dedicada* -> Basica, Standart, Premium V1,V2 e V3 , recusos dedicados ao plano de servilo, quanto maior o nível maior o numero de maquinas disponivel
    - *Isolado* -> Camada dedicada em redes virtuas dedicadas, capacidade máxima de expansão
    - *Consumo* -> Apenas para aplicativos de funções, dimenciona conforme a carga.


#### Implantar Serviço de Aplicativo do Azure
Suporte a implantação Automática ou Manual

- **Impantação Automatizada**
Implantação continua - push -> copilação na nuvem -> teste -> geração de versão e implantação  para Azure Devops, GitHub e Bitbucket
- **Impantação Manual**
Enviar o Código manualmente para o Azure - Git, CLI (az webapp up), zio usando curl para subir o pacote, FTP/S para subir o codigo
- **Slots de Implantação**
Recomendado quando implantar um novo build em produção, ambiente de prepraro e trocar para produção - eliminando o tempo de inatividade


#### Autenticação e a autorização no Serviço de Aplicativo
Conectar usuários e acessar dados gravando mínímo ou nenhum código nos aplicativos
Facilitar e agilizar os procesos ao fornecer autênticação pronta para uso com provedores de identidade federada.
**Provedoores de Logon**
- Microsoft
- Facebook
- Google
- Twitter
- Open ID Connect

O Modulo de Autentição trata autenticação de usuários com provedor, valida armazena e atualiza os tokens. Gerencia a sessão autenticada e injeção de informações de identidade em cabeçalhos de solicitação. 
Em Linux e Conteiners o modulo de autenticação e autorização é executado em um container separado.

**Fluxo de Autenticação**
- *Sem SDK do Provedor* -> delega o logon federado ao Serviço de Aplicativo (Aplicativo Navegador) - O codigo do servidor gerencia o processo do logon - Fluxo do servidor
- *Com o Provedor SDK* -> o aplicativo assina os usuários no provedor manualmente e em seguida envia o token de autenticação para o Serviço do aplicativo (fluxo do cliente) APIS , Functions, Java Script e Dispositivos Moveis
