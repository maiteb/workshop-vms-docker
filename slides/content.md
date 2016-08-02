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

>  Uma série de computadores de configurações "mais simples", porém tecnologicamente homogêneos, conectados por uma rede mais rápida e próxima do que uma rede local, com baixa latência, trabalhando em conjunto como um único e integrado recurso computacional.

Note: Mais simples => Mais barato $

---

## Computação em grade

> Não existe nenhuma premissa tecnológica entre os nós integrantes do
> sistema. Interessante saber que recursos de diferentes organizações
> são reunidos para permitir a colaboração de um grupo de usuários,
> formando uma *organização virtual*.

Note: Pessoas pertencentes à mesma organização virtual tem direitos de
acesso aos recursos fornecidos por ela. 

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

---

## Cloud computing

Pela [AWS](https://aws.amazon.com/pt/what-is-cloud-computing/)
> Usando o princípio de computação em grade, se refere a entrega de
> recursos computacionais (por exemplo: memória, processamento, armazenamento),
e aplicativos pela internet sob demanda.

---

## Tipos de cloud computing

* Infraestrutura como Serviço (IaaS)
* Plataforma como Serviço (PaaS)
* Software como Serviço (SaaS)

Note: 1. Amazon EC2, 2. AWS Elastic Beanstalk, Heroku, 3. Google Drive

---

## Provedores de nuvens públicas

* Amazon Web Services;
* DigitalOcean;
* Rackspace;

---

## Nuvens privadas

* Openstack
  * HP Helion
  * RedHat Openstack
  * Ubuntu Cloud
  * Rackspace;

---

## Virtualização

Pela
[RedHat](http://www.redhat.com/f/pdf/virtualization/gunner_virtual_paper2.pdf):

> Permitir rodar múltiplas instâncias de sistemas
> operacionais concorrentemente em um único computador, separando
> hardware a partir de um único sistema operacional.

---

## Virtualização


Pela
[RedHat](http://www.redhat.com/f/pdf/virtualization/gunner_virtual_paper2.pdf):

> Cada SO convidado é gerenciado pelo hypervisor, que controla o uso de
> CPU, memória e armazenamento de cada uma das máquinas virtuais

---

## Virtualização

![Virtualização](http://www.vcritical.com/wp-content/uploads/2009/04/hw_vmw_os_app.png)

_Fonte: [VCritical](http://www.vcritical.com/)_

---

# Hypervisor

Por
[UFRJ](http://www.gta.ufrj.br/grad/08_1/virtual/OqueohypervisorouVMM(VirtualMachineMonit.html)

> Camada de software entre o hardware e o SO, responsável por abstrair a
> máquina virtual para o SO convidado, ou seja, ele é quem executa ou
> simula executar instruções (privilegiadas ou não) requisitadas pelo SO
> visitante.

---

## Tipos de hypervisor

* Nativo;
* Hosted.

Note: 1. Roda direto sobre o hardware, exemplo Xen, VMware ESX; 2.
Executa sobre um SO para oferecer a funcionalidade descrita: VirtualBox,
QEMU, VMware.

---

## VM como código

[Vagrant](https://www.vagrantup.com/docs/getting-started/project_setup.html)

(Agora vamos brincar um pouco)

---

## Vagrant

Comandos úteis

```sh
$ vagrant init hashicorp/trusty64
$ vagrant up
$ vagrant provision
$ vagrant halt
$ vagrant destroy
```
