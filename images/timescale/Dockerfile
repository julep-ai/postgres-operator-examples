# 1) Match PG major & UBI base to your cluster
FROM registry.developers.crunchydata.com/crunchydata/crunchy-postgres:ubi9-17.6-2534

# 2) Elevate for package install
USER 0

# 3) Add Timescale repo + install the PG17 build
#    (Timescale publishes EL9 RPMs; install using their repo script or add the repo file)
RUN curl -sSL https://packagecloud.io/install/repositories/timescale/timescaledb/script.rpm.sh | bash \
 && microdnf -y install timescaledb-2-postgresql-17 \
 && microdnf clean all

# 4) Drop back to the image’s non-root user
USER 26
