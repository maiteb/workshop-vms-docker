## Cloud computing, máquinas virtuais, contâineres e Docker

Maitê Balhester

mbalhest@thoughtworks.com

---

## Um pouco sobre mim

* Cientista da Computação pela UFABC
* +10 anos programando
* +5 anos no mercado
* +1 devops
* Github: [@maiteb](http://github.com/maiteb)

---

## Sistemas distribuídos

Tanenbaum (2007):

> "Um sistema distribuído é um conjunto de computadores independentes
> que se apresenta a seus usuários como um sistema único e coerente."

Note: A organização interna e a diferença entre os vários computadores e
como se comunicacam deve ser transparente ao usuário.

---

## Cluster de computadores

>  Uma série de computadores de configurações "mais simples" conectados por uma rede mais rápida e próxima do que uma rede local, com baixa latência, trabalhando em conjunto como um único e integrado recurso computacional.

Note: Mais simples => Mais barato $

---

## Transparência da distribuição

* Acesso
* Localização
* Migração
* Relocação
* Replicação
* Concorrência
* Falha

Note: oculta diferenças na representação de dados e modo de acesso a
um recurso; o lugar onde está localizado; a movimentação de um recurso
para outra localização - enquanto em uso ou não; se pode ser
compartilhado entre usuários concorrentes e a falha e recuperação de um
recurso.

---

## Escalabilidade

* Tamanho: fácil adicionar mais usuários e recursos;
* Geografia: recursos e usuários podem estar distantes uns dos outros;
* Administrativo: fácil de administrar, mesmo envolvendo muitas
  organizações administrativas;

---

## Arquiteturas

* Em camadas
* Baseada em objetos
* Centrada em dados
* Baseada em eventos

---

## Cliente-Servidor

* Servidor: processo que implementa um serviço específico;
* Cliente: processo que requisita um serviço fornecido por um servidor.

---

## Cliente-Servidor

![Cliente-Servidor](https://cdn.tutsplus.com/gamedev/uploads/2013/08/img1_server_client.png)

_Fonte: [Envatotuts](http://gamedevelopment.tutsplus.com/)_

