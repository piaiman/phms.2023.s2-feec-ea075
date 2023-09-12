# `Manta e sistema de controle de aquecimento para procedimentos hospitalares.`
# `Blanket and heating control system for hospital procedures`

## Apresentação

O presente projeto foi originado no contexto das atividades da disciplina de graduação *EA075 - Introdução ao Projeto de Sistemas Embarcados*, 
oferecida no segundo semestre de 2023, na Unicamp, sob supervisão da Profa. Dra. Paula Dornhofer Paro Costa, do Departamento de Engenharia de Computação e Automação (DCA) da Faculdade de Engenharia Elétrica e de Computação (FEEC).

 |Nome  | RA | Curso|
 |--|--|--|
 |Guilherme Lehmann Concentino  | 173805  | Eng. Elétrica |
 |Pedro Henrique Moraes Dos Santos  | 243528 | Eng. Elétrica |

## Descrição do Projeto

Visando uma melhor qualidade de vida e humanização no tratamento dos pacientes de ambientes hospitalares, desenvolvemos uma manta aquecedora para controle de temperatura.

Entre alguns procedimentos onde controle de temperatura continuo é importante, temos: procedimentos como transfusão de concentrado de hemácias requerem o aquecimento antes de serem aplicadas nos pacientes para evitar a coagulação; para apoio na analgesia da pele suprapúbica quando de insere um DIU; aquecimento por contado para recém-nascidos nos primeiros minutos de vida, além do condicionamento térmico de uma bolsa de ocitocina antes de infundi-la no pôs parto (período de grenberg), mas também visando o conforto térmico do paciente dado que frio de clínicas e hospitais é necessário, porém desagradável para muitos.

O produto possui dois componentes: um controlar para aquecimento e a malha resistiva que pode ter diferentes tamanhos, sendo que um controlado pode ser usado para malhas de diferentes medidas desde peça de 20x20 cm até peças de 2x1 m transmitindo o calor de forma constante. Ele trabalha com pré-set de 37,5 °C no equilíbrio, além de contar com termômetro que acompanhar a temperatura do paciente e quantifica o quanto de calor deverá ser transmitido. Além disso, ele conta com modos rápido e lente de aquecimento. E também, conta com alimentação por tomada e baterias.

## Descrição Funcional

 O controle de temperatura é feito a partir de um microcontrolador, e a temperatura será configurada pelo operador e controlada por sensores de temperatura. Também deverá:

*É interessante conter um pré-set de temperatura em 37,5°C, mas que seja possível alterar;
*É importante que tenha dois modos de aquecimento, um rápido e outro lento;
*Que não faça barulho;
*Que tenha um indicador de temperatura do paciente, além de ter um sinalizador onde demonstre se paciente não está conseguindo manter o calor sem o equipamento;
*Que seja inteligente e monitore o paciente após ter atingido a homeostase, mas também que em caso de queda de temperatura fora da faixa adequada, volte a aquecer e avise a equipe;
*O dispositivo não deve oferecer risco de queimaduras aos pacientes, devendo trabalhar na região de homeostase, com temperatura uniforme;
*Caso dispositivo tenha contato direto com a pele, deverá oferecer o menor risco de contaminação;
*Em caso de problema a equipamento precisa se autodesligar e sinalizar o problema por uma IHM;
*Não usar métodos invasivos;
*Confortável ao toque. em caso de contato.

### Funcionalidades

* O sistema será capaz de identificar a temperatura corporal do usuário, a temperatura ambiente e a temperatura interna do cobertor;
* Será possível selecionar a temperatura desejada atarvés de uma interface com o operador;
* Será possível monitorar todas as temperaturas pela interface com o operador;
* Deve contar com sistema de aquecimento lento e rápido;
* Um timer para ajuste de períodos de aquecimento;
* Proteção sobre aquecimento;
* Sinalizadores para situações emergências;
* Deverá ter um indicador de nível de bateria.

### Configurabilidade

Será configurada a temperatura que é desejada entre cobertor e usuário. Pode se adaptar a diferentes malhas de tamanhos distuntos; pode trabalhar com a  rede AC convencional  e com baterias.

### Eventos

O sistema deve ler as temperaturas do sistema e ajustar a corrente fornecida às resistências para manipular a temperatura gerada pela malha térmica.O ciclo de operação do sistema seguirá a seguinte lógica:

1. Operador deverá verificar qual a forma de alimentação será usada, AC ou bateria.
2. Ligar a chave geral de operação do equipamento para ligá-lo.
3. Após isso, o microcontrolador deverá detectar se a manta térmica está conectada a ele.
   
       3-A. Caso a condição anterior seja cumprida, a próxima etapa, caso não seguirá o item 3-B.
  
       3-B. O controlador deverá indicar que existe um problema com a malha, ficando travado nesta condição, sendo liberado com o reset (liga e desliga geral do equipamento).
  
4. O controlador verificará se os sensores de temperatura estão conectavados e prontos para operar, caso contrário ocorrerá a mesma situação do item 3-B indicando qual sensor apresenta problemas.
5. Dado que todas as condições foram atendidas a IHM liberada para configuração.
       5-A. O controlador deverá permitir o ajuste de temperatura de aquecimento, sendo que por padrão ele deve iniciar com a temperatura de 37,5 C.
       5-B. Após realizar o ajuste de temperatura, deverá ser escolher o modo de aquecimento rápido e lento.
       5-C Por fim, ajustar o tempo de operação.

6. Feito isso, o operador deve apertar o botão para iniciar o ciclo de aquecimento.

7. Durante o ciclo de aquecimento o sistema atuará com uma rotina de inteligente de monitoramento do paciente e temperatura. Contudo, a algumas condições poderão gera a interrupção do ciclo, entre elas:

       7-A.Sobre aquecimento do paciente;
   
       7-B. Sobre corrente no sistema;
   
       7-C. Dectação de fuga de corrente;
   
       7-D. Baixo ganho de temperatura;

8. Após o ciclo de aquecimento, o controlador deverá sinalizar que o ciclo foi finalizado, mostrando parâmetros de tempo médio de aquecimento.
9.  Permitirá que seja feito um novo ciclo.


## Descrição Estrutural do Sistema - Não iniciado
> Junto com a descrição do comportamento do sistema, deve-se especificar, em nível de bloco ou sistema, a estrutura necessária 
> para captar os eventos do mundo externo, para alojar e processar o programa de tratamento de eventos, e para atuar sobre o mundo externo.
>
> Para essa descrição recomenda-se a criação de diagramas de blocos.
> Nesse diagrama, devem ser destacados os blocos funcionais que compõem o sistema, incluindo uma síntese das funcionalidades de cada bloco.
> Além disso, deve-se esclarecer também o relacionamento entre estes blocos, incluindo os principais sinais de comunicação entre
> os blocos de forma a assegurar a execução de todas as tarefas que o sistema deve realizar.
> 
> Você sabia? Ferramentas como o `draw.io` permitem integração com o Github.
> 

## Referências
> Seção obrigatória. Inclua aqui referências utilizadas no projeto.


https://www.saude.df.gov.br/documents/37101/87400/Protocolo+Transfusional+%E2%80%93+Indica%C3%A7%C3%A3o+de+Hemocomponentes.pdf/51637b5a-167b-1022-ccfe-fb588c34a56c?t=1648647623844