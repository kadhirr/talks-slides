---
theme: 'academic'
title: 'Distributed Machine Learning with Cloud'
lineNumbers: true
monaco: 'build'
highlighter: 'prism'
colorSchema: 'dark'
fonts:
    mono: 'FiraMono NF Regular'
---
# Distributed Machine Learning with Cloud Technologies



---

# Our Problem

<v-clicks>

- The size of Datasets are large

- Training Time is getting longer

- Compute Powers of workstations are not enough
</v-clicks>


---
layout: center
---
## Solution?

<style>
    h1 {
        @apply text-teal-500 ;
    }
</style>

<v-click>

<h1>Distributed Machine Learning/<br>Deep Learning</h1>

</v-click>

---

# Distributed Learning

There are two types of distributed Learning (in Deep Learning)

<v-click>

1. Model Parallelism
2. Data Parallelism

</v-click>

---
layout: figure-side
figureUrl: './assets/model_parallelism.png'
figureCaption: 'Model Parallelism'
---



# Model Parallelism

<v-click>
<div class="my-35">
Model parallelism is used when your model has too many layers to fit into a single GPU and hence different layers are trained on different GPUs.
</div>
</v-click>

---
layout: figure-side
figureUrl: '/assets/data_parallelism.png'
figureCaption: 'Data Parallelism'
---



# Data Parallelism

<v-click>
<div class="my-35">
Data parallelism, the more common of the two, achieves speed-up by splitting the data into different partitions. The model is run simultaneously on multiple GPUs using different data partitions.
</div>
</v-click>

---
layout: center
---


# Now, lets talk about <span>Cloud</span>

<style>
    h1 {
        font-size: 3rem !important;
    }
    span {
        @apply text-blue-500 underline;
    }
</style>

---

# Scaling

<div class="flex justify-around">

<v-click>

<div>

## Vertical Scaling

![Verical Scaling](/assets/vertical_scaling.png)

</div>

</v-click>

<v-click>

<div>

## Horizontal Scaling

![Horizontal Scaling](/assets/horizontal_scaling.png)

</div>

</v-click>

</div>

<style>
    img {
        width: 20vw;
        @apply my-15;
    }
</style>

---
layout: center

---

# Our Solution to Distributed Learning

<v-clicks>

- Dask

- Docker

- Container Orchestration

</v-clicks>

---

# Docker <logos-docker-icon />

<v-clicks>

- OS-level virtualization to deliver software in packages called <span class="underline">containers</span>.

- Isolated, Lightweight Environment.

- Portable

- Primarily used to provide self contained environments for companies to ease their build to deployment cycle.

</v-clicks>

---

# Docker vs VMs

<v-click>

![Docker vs VMs](/assets/dockerimg.webp)

</v-click>

---

# Docker Architecture

<v-click>

![Docker Architecture](/assets/dockerarch.webp)

</v-click>

---

# Dockerfile <logos-docker-icon /><icon-park-config />

- Dockerfiles are used to create images

<br /><br /><br />

```dockerfile {1|2|3|4|5|7|8}
# syntax=docker/dockerfile:1
FROM node:12-alpine
RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000

```

----

# Container Orchestration

<v-clicks>

- Automation of much of the operational effort required to run containerized workloads and services. 

- Provides tools needed to manage a container's lifecycle, including provisioning, deployment, scaling (up and down), networking, load balancing and more.

- Examples
    - <logos-kubernetes /> Kubernetes 
    - <logos-openshift /> Openshift
    - <logos-nomad-icon /> Hashicorp Nomad

</v-clicks>

---
layout: center
---

# Dask <simple-icons-dask />

<v-clicks>

> Dask is a flexible open-source Python library for parallel computing. Dask scales Python code from multi-core local machines to large distributed clusters in the cloud.

<em><u>Dask Does Data Parallelism</u></em>


</v-clicks>

---
layout: figure
figureCaption: 'Dask Overview'
figureUrl: 'https://raw.githubusercontent.com/kadhirr/talks-slides/main/cognitive-dcc/assets/daskoverview.jpg'
---

# Dask <simple-icons-dask />


---

# Dask <simple-icons-dask />

```python {1-2|4-5|7|all}
from dask.distributed import Client
import dask

client = Client(n_workers=2, threads_per_worker=2, memory_limit="1GB")
client

df = dask.datasets.timeseries()

df2 = df[df.y > 0]
df3 = df2.groupby("name").x.std()
df3

```
<v-click> 

Dask Dataframes lazily load data, meaning data is only loaded when computation is required.

</v-click>

---
layout: center
---

# DEMO

---
layout: center
---

![Profile Photo](/assets/pfp.jpg)
# Kadhirravan R
## Find me at 0xapollo.me

<style>
    img {
        border-radius: 50%;
        height: 125px;
        width: 125px;
        object-fit: cover;
    }
</style>
