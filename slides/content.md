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

Configuração de imagem inicial


```ruby
Vagrant.configure("2") do
  config.box = "ubuntu/trusty64"
end
```

---

## Vagrant

Configurações de rede

```ruby
Vagrant.configure("2") do |config|
  config.vm.network :forwarded_port, guest: 80, host: 9090
end
```
_A porta 80 do SO convidado é encaminhada para a porta 9090 do host_

---

## Vagrant

Configurações de rede

```ruby
Vagrant.configure("2") do |config|
  config.vm.network "private_network", ip: "192.168.50.4"
end
```

_A VM está acessível em uma rede privada com IP 192.168.50.4_

---

## Vagrant

Provisionamento


```ruby
Vagrant.configure("2") do |config|
 config.vm.provision "shell", inline: <<-SHELL
   sudo apt-get update
   sudo apt-get install -y apache2
 SHELL
end
```

_Após a criação da máquina, irá executar os comandos especificados_

---

## Vagrant

```ruby
Vagrant.configure("2") do |config|
  config.vm.provision "shell", path: "script.sh"
end
```

_Após a criação da máquina, irá executar ```script.sh```_

---

## Vagrant

Comandos úteis

```sh
$ vagrant init ubuntu/trusty64
$ vagrant up
$ vagrant ssh
$ vagrant provision
$ vagrant halt
$ vagrant destroy
```

---

## Contâineres

Por [Docker](https://www.docker.com/what-docker#/VM):

> Um contâiner contém a aplicação e suas dependências, mas compartilhar
> o kernel com outros contâineres, sendo um processo isolado em  _user space_ do sistema operacional host.

---

## Contâineres

![Contâineres](https://www.docker.com/sites/default/files/WhatIsDocker_3_Containers_1.png)

_Fonte: [Docker](http://www.docker.com/)_

---

## Docker

```sh
$ docker run hello-world
$ docker ps -a
```

---

## Docker

```sh
$ docker run docker/whalesay cowsay boo
Unable to find image 'docker/whalesay:latest' locally
latest: Pulling from docker/whalesay
e9e06b06e14c: Pull complete
a82efea989f9: Pull complete
37bea4ee0c81: Pull complete
07f8e8c5e660: Pull complete
676c4a1897e6: Pull complete
5b74edbcaa5b: Pull complete
1722f41ddcb5: Pull complete
99da72cfe067: Pull complete
5d5bd9951e26: Pull complete
fb434121fc77: Already exists
Digest:
sha256:d6ee73f978a366cf97974115abe9c4099ed59c6f75c23d03c64446bb9cd49163
Status: Downloaded newer image for docker/whalesay:latest
```

---

## Docker

Executar interativamente

```sh
$ docker run -it ubuntu bash
```

---

## Docker

Criando sua própria imagem

```sh
# Dockerfile
FROM ubuntu:14.04

RUN apt-get update
RUN apt-get install -y nginx
RUN echo 'Container criado no workshop da SECOMP' \
    >/usr/share/nginx/html/index.html

CMD [ "nginx", "-g", "daemon off;" ]

EXPOSE 80

```

---

## Docker

Para construí-la:

```sh
$ docker build . --tag nome_da_imagem
```

---

## Docker

Para executá-la:

```sh
$ docker run -it nome_da_imagem
```

É possível mapear portas do container para o host:
```sh
$ docker run -p 80:8080 -it nome_da_image
```

---

## Docker

Para listar todas as imagens locais:

```sh
$ docker images
```

---

## Docker

Para se conectar à um container em execução:

```sh
$ docker attach id_do_container
```

---

## Docker

Para executar um comando em um container em execução:

```sh
$ docker exec -it id_do_container comando
```

Exemplo de uso:
```sh
$ docker exec -it id_do_container bash
```

---

## Docker

Acessar logs do container:

```sh
$ docker logs id_do_container
```

---

## Docker

Atualizar um container e criar uma nova imagem:

```sh
$ docker commit id_do_container [--tag nome_da_imagem]
```

---

## Docker

Parar um container em execução:

```sh
$ docker stop id_do_container
```

Para matá-lo:

```sh
$ docker kill id_do_container
```
