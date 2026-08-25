\# Aula 2 - Memórias e Processadores



Considerando os tipos de memórias e processadores visto em aula, busque informações sobre as arquiteturas de processadores que estão disponíveis nos servidos de cloud computing (AWS, GCP, Azure, Digital Ocean, Oracle, etc) e responda



\## Quais as arquiteturas que estão disponíveis



AWS x86-64 com processadores Intel e AMD e ARM64 pros processadores Graviton desenvolvidos pela própria AWS.



Oracle x86-64 com processadores Intel e AMD e ARM64 pros processadores Ampere Altra e AmpereOne.



Azure  x86-64 com processadores Intel e AMD e ARM64 principalmente Ampere Altra e os processadores Microsoft Cobalt.



\## Considerando que boa parte dos recursos são os mesmos, qual a diferença de preço entre elas



&#x20;Provedor  Máquina           Cpu     Ram    Processador  Preço(mês) 

\--------------------------------------------------------------------

&#x20;AWS       t3a.medium        2 vCPU  4 GiB  AMD EPYC     US$ 27,45  

&#x20;Oracle    E5 Flex           2 vCPU  4 GiB  AMD EPYC     US$ 27,74  

&#x20;Azure     Standard\_B2ls\_v2  2 vCPU  4 GiB  Intel Xeon    US$ 30,37 



\## Existe algum serviço que oferece alguma arquitetura que os outros não oferecem



AWS

Possui tecnologias próprias como o AWS Nitro System e os processadores Graviton (ARM64), desenvolvidos pela própria AWS.



Oracle

Oferece x86-64 e ARM64, mas utiliza processadores de terceiros, como Intel, AMD e Ampere.



Azure

Oferece x86-64 e ARM64, incluindo processadores próprios Microsoft Cobalt e CPUs de IntelAMD.



\## O que cada serviço oferece para armazenamento



AWS

Oferece S3 (objetos), EBS (blocos) e EFS (arquivos), atendendo desde armazenamento de objetos até discos para VMs e sistemas de arquivos compartilhados. 



Oracle

Oferece Object Storage (objetos), Block Volumes (blocos) e File Storage (arquivos), além de uma opção específica de Archive Storage para dados de longo prazo. 



Azure

Oferece Blob Storage (objetos), Managed Disks (blocos) e Azure Files (arquivos), além do Data Lake Storage voltado para análise de grandes volumes de dados. 



\## Qual a diferença entre os tipos de armazenamento oferecidos dentro do mesmo provedor



AWS

S3 é para objetos, EBS funciona como disco para VMs e EFS permite arquivos compartilhados. A diferença principal está na forma de acesso e no uso.



Oracle

Object Storage é para objetos, Block Volume para discos de VMs e File Storage para arquivos compartilhados. Também há Archive Storage, voltado para dados acessados raramente.



Azure

Blob Storage é para objetos, Managed Disks para discos de VMs e Azure Files para arquivos compartilhados. O Data Lake Storage é otimizado para grandes volumes de dados e análise.



\## Faça uma comparação dos serviços de armazenamento oferecidos entre os provedores.



AWS

Oferece S3 (objetos), EBS (blocos) e EFS (arquivos). É a que possui a maior variedade de serviços adicionais de armazenamento, como FSx e Storage Gateway. 



Oracle

Oferece Object Storage (objetos), Block Volume (blocos) e File Storage (arquivos), além de Archive Storage para dados acessados raramente. 



Azure

Oferece Blob Storage (objetos), Managed Disks (blocos) e Azure Files (arquivos), além de opções especializadas como Azure NetApp Files e Data Lake Storage.

