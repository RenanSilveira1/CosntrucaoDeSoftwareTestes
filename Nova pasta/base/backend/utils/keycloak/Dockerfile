# A imagem é iniciada com um Linux um pouco mais completo do que utilizado na imagem do Keycloak, apenas para permitir a instalação do curl, que é necessário para o health checking do container do Keycloak e não existe na sua imagem
FROM redhat/ubi9:9.3 AS ubi9

RUN dnf install --installroot /mnt/rootfs curl --releasever 9 --setopt install_weak_deps=false --nodocs -y; dnf --installroot /mnt/rootfs clean all

# A imagem do Keycloak utiliza um Linux bem enxuto, sen nenhum utilitário, ou seja, sem o curl
FROM quay.io/keycloak/keycloak:24.0

# O root do Linux ubi9 é montado no container do Keycloak, ou seja, ele passa a ter todos os utilitários do Linux ubi9, inclusive o curl
COPY --from=ubi9 /mnt/rootfs /