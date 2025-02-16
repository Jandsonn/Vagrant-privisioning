# Vagrant Configuration

Este repositório contém dois arquivos de configuração do Vagrant (`Vagrantfile` e `Vagrantfile2`) para provisionar múltiplas máquinas virtuais usando VirtualBox.

## Vagrantfile

O `Vagrantfile` configura um ambiente com as seguintes máquinas virtuais:

- **Load Balancer**:
  - Hostname: `lb`
  - Box: `ubuntu/bionic64`
  - IP: `10.0.1.3`
  - Provisionamento: Ansible (`playbook.yml`)

- **Application Servers**:
  - `app1`:
    - Hostname: `app1`
    - Box: `ubuntu/bionic64`
    - IP: `10.0.1.4`
    - Provisionamento: Ansible (`playbook.yml`)
  - `app2`:
    - Hostname: `app2`
    - Box: `ubuntu/bionic64`
    - IP: `10.0.1.5`
    - Provisionamento: Ansible (`playbook.yml`)

- **Database Server**:
  - Hostname: `db`
  - Box: `ubuntu/bionic64`
  - IP: `10.0.1.6`
  - Provisionamento: Ansible (`playbook.yml`)

## Vagrantfile2

O `Vagrantfile2` configura um ambiente com as seguintes máquinas virtuais:

- **Application Server 1**:
  - Hostname: `hostA`
  - Box: `centos/7`
  - IP: `10.0.1.4`

- **Application Server 2**:
  - Hostname: `hostB`
  - Box: `centos/7`
  - IP: `10.0.1.5`

- **Database Server**:
  - Hostname: `hostC`
  - Box: `centos/7`
  - IP: `10.0.1.6`

## Configurações Comuns

- **Memória**:
  - `Vagrantfile`: 512 MB
  - `Vagrantfile2`: 256 MB

- **Chave SSH**:
  - `insert_key` está definido como `false` para ambos os arquivos.

## Como Usar

1. Clone o repositório:
   ```sh
   git clone https://github.com/Jandsonn/Vagrant-privisioning.git
   cd Vagrant-privisioning


   PARA PROVISIONAR, APÓS TER O VAGRANT CONFIGURADO EM SUA MÁQUINA, UTILIZE OS SEGUINTES COMANDOS PARA PROVISIONAR:
   Inicie o Vagrant:

   vagrant up

   E para destruir os recursos use:
   Para destruir as máquinas virtuais:

   vagrant destroy -f
