# ceph-k8s-backup

Estructura del REPO (como todo un DevOps mexicano) ceph-k8s-backup/

ceph-k8s-backup/
├── README.md                 ← TU CARTA DE PRESENTACIÓN
├── LICENSE                   ← MIT (o GPL si es para HPC)
├── .github/
│   └── workflows/
│       └── ci.yml            ← GitHub Actions: lint + test
├── backup/
│   ├── __init__.py
│   ├── metadata.py
│   ├── metrics.py
│   ├── backup.py
│   └── restic_job.yaml      ← Template del Job
├── charts/
│   └── ceph-backup/         ← Helm chart (opcional, pero pro)
├── scripts/
│   └── install-termux.sh    ← ¡Para tus carnales con Android!
├── docs/
│   └── architecture.md
└── pyproject.toml           ← o requirements.txt

# Ceph K8s Backup (Restic + Prometheus)  
**Backups automáticos de volúmenes Ceph RBD en Kubernetes**  
*Hecho en México con Termux, café y pura pasión por el HPC*

![backup-demo](docs/demo.gif)

---

## ¿Por qué funciona?

- **Descubre** PVCs con anotación `cephbackup.hpc.nyu.edu/backup: "true"`
- **Respaldos diarios** con Restic a S3/MinIO
- **Métricas Prometheus** → Grafana
- **Throttling inteligente** → 1/24 de backups por hora
- **Limpieza automática** de Jobs

---

## Instalación en **Termux** (Android)

```bash
pkg update && pkg install git python clang make
pip install kubernetes prometheus-client opentelemetry-api

# Clona y corre métricas
git clone https://github.com/RAMON_CERDA/ceph-k8s-backup
cd ceph-k8s-backup
python -m backup.metrics --table

Autor@RAMON_CERDA

 – DevOps desde el rancho, con Termux y un Galaxy A52"Si Ceph se cae, mis backups no."


