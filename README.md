<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:000000,50:0D1117,100:000000&height=210&section=header&text=OMKAR%20BIRADAR&fontSize=48&fontColor=39FF14&fontAlignY=38&desc=DevOps%20Engineer%20%2F%2F%20Linux%20%2B%20Cloud%20%2B%20Automation&descAlignY=58&descSize=16&animation=fadeIn" width="100%"/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=17&duration=2600&pause=1000&color=39FF14&center=true&vCenter=true&width=780&lines=%24%20systemctl%20status%20omkar.service;%E2%97%8F%20omkar.service%20-%20loaded%20(enabled%3B%20vendor%20preset%3A%20always-on);%20%20%20Active%3A%20active%20(running)%20since%202021%3B%20%20%20Mission%3A%20automate%20everything%2C%20break%20nothing" alt="terminal typing"/>

<br/>

<a href="https://www.linkedin.com/in/omkar-biradar-457725245"><img src="https://img.shields.io/badge/LINKEDIN-000000?style=for-the-badge&logo=linkedin&logoColor=39FF14&labelColor=0D1117"/></a>
<a href="mailto:biradaromkar.4176@gmail.com"><img src="https://img.shields.io/badge/EMAIL-000000?style=for-the-badge&logo=gmail&logoColor=39FF14&labelColor=0D1117"/></a>
<a href="https://leetcode.com/u/Omkar_0212/"><img src="https://img.shields.io/badge/LEETCODE-000000?style=for-the-badge&logo=leetcode&logoColor=39FF14&labelColor=0D1117"/></a>
<a href="https://github.com/dev-omkarbiradar"><img src="https://img.shields.io/badge/GITHUB-000000?style=for-the-badge&logo=github&logoColor=39FF14&labelColor=0D1117"/></a>

<br/><br/>

<img src="https://img.shields.io/badge/OS-Arch_Linux-000000?style=flat-square&logo=archlinux&logoColor=39FF14&labelColor=0D1117"/>
<img src="https://img.shields.io/badge/SHELL-bash%20%2F%20zsh-000000?style=flat-square&logo=gnubash&logoColor=39FF14&labelColor=0D1117"/>
<img src="https://img.shields.io/badge/EDITOR-Neovim-000000?style=flat-square&logo=neovim&logoColor=39FF14&labelColor=0D1117"/>
<img src="https://img.shields.io/badge/UPTIME-3%2B_years-000000?style=flat-square&logo=linux&logoColor=39FF14&labelColor=0D1117"/>

</div>

<br/>

## `$` neofetch

```text
                  -`                    omkar@devops-machine
                 .o+`                   ---------------------
                `ooo/                   OS: Arch Linux x86_64
               `+oooo:                  Host: Cloud-Native Infrastructure
              `+oooooo:                 Kernel: 6.6.0-shipfast
              -+oooooo+:                Uptime: 3+ years, minimal downtime
            `/:-:++oooo+:               Shell: bash 5.2 + zsh (tmux inside)
           `/++++/+++++++:              Role: DevOps Engineer / Full-Stack Dev
          `/++++++++++++++:             Location: Pune, India
         `/+++ooooooooooooo/`           CPU: Problem-Solving Core (8) @ inf GHz
        ./ooosssso++osssssso+`          Memory: 12GB Coffee / inf GB Curiosity
       .oossssso-````/ossssss+`         Packages: docker, k8s, terraform, git
      -osssssso.      :ssssssso.        WM: CI/CD Pipelines
     :osssssss/        osssso+++.       Achievements: 2x Hackathon Winner
    /ossssssss/        +ssssooo/-
  `/ossssso+/:-        -:/+osssso+-
 `+sso+:-`                 `.-/+oso:
`++:.                           `-/+/
.`                                 `/
```

<br/>

## `$` cat about.md

```yaml
name: Omkar Biradar
role: DevOps Engineer | Full-Stack Developer
location: Pune, India
mission: Ship faster, break less, automate everything
focus:
  - Designing CI/CD pipelines that ship with confidence
  - Containerizing & orchestrating cloud-native applications
  - Infrastructure as Code — repeatable, versioned, disposable
  - Living inside a terminal — tmux, vim, and a lot of grep
currently_exploring: [Kubernetes, System Design, Cloud Cost Optimization]
achievement: 🏆 Winner — TechXcelerate Hackathon @ BITS Pilani (SaaS Category)
fun_fact: I automate things twice, just to make sure the automation works
```

<br/>

## `$` systemctl status devops-pipeline.service

```text
● devops-pipeline.service - Continuous Integration & Deployment
     Loaded: loaded (/etc/systemd/system/devops-pipeline.service; enabled)
     Active: active (running) since Mon 2021-01-01

     ├─ code.service          active (running)   git commit && git push
     ├─ build.service         active (running)   GitHub Actions CI trigger
     ├─ test.service          active (running)   unit + integration suite
     ├─ containerize.service  active (running)   docker build -t app:latest .
     ├─ registry.service      active (running)   docker push → registry
     ├─ deploy.service        active (running)   kubectl apply -f deploy/
     └─ monitor.service       active (running)   prometheus + grafana alerts

     Main PID: 1337 (pipeline)
     CGroup: /system.slice/devops-pipeline.service
     Status: "All systems operational. Zero manual steps."
```

<br/>

<details>
<summary><b>$ man devops-pipeline (click to expand architecture)</b></summary>
<br/>

```mermaid
%%{init: {'theme':'dark', 'themeVariables': {'primaryColor':'#0D1117','primaryTextColor':'#39FF14','primaryBorderColor':'#39FF14','lineColor':'#39FF14','secondaryColor':'#161B22','tertiaryColor':'#000000'}}}%%
flowchart LR
    A["👨‍💻 Local Dev"] --> B["📦 git push"]
    B --> C["⚙️ CI Build"]
    C --> D["🧪 Test Suite"]
    D --> E{"exit code 0?"}
    E -- no --> A
    E -- yes --> F["🐳 docker build"]
    F --> G["📤 registry push"]
    G --> H["☸️ kubectl apply"]
    H --> I["📊 monitor / alert"]
    I -.rollback on failure.-> A
```

</details>

<br/>

## `$` pacman -Qe --grep devops

```text
aws                  24.1-1     [installed]
azure-cli            2.65-1     [installed]
gcloud-sdk            492-1     [installed]
docker                27.3-1    [installed]
kubernetes-cli         1.31-1   [installed]
terraform              1.9-1    [installed]
github-actions-runner  stable   [installed]
git                    2.46-1   [installed]
nodejs                 22.4-1   [installed]
python                 3.12-1   [installed]
postgresql             16.4-1   [installed]
mongodb                7.0-1    [installed]
redis                  7.4-1    [installed]
nginx                  1.27-1   [installed]

14 packages installed. system is up to date.
```

<div align="center">

**Cloud & Infra**
<br/>
<img src="https://skillicons.dev/icons?i=aws,gcp,azure,terraform,vercel" height="46"/>

**Containers & Orchestration**
<br/>
<img src="https://skillicons.dev/icons?i=docker,kubernetes" height="46"/>

**CI/CD, Shell & OS**
<br/>
<img src="https://skillicons.dev/icons?i=githubactions,git,github,linux,bash,vim" height="46"/>

**Backend & APIs**
<br/>
<img src="https://skillicons.dev/icons?i=nodejs,express,fastapi,flask,python,js" height="46"/>

**Databases**
<br/>
<img src="https://skillicons.dev/icons?i=mongodb,postgres,mysql,redis" height="46"/>

**Frontend**
<br/>
<img src="https://skillicons.dev/icons?i=react,tailwind,html,css" height="46"/>

</div>

<br/>

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:000000,100:0D1117&height=3&width=100%25" width="100%"/>

## `$` ls -la ~/projects/

```text
drwxr-xr-x  omkar devops  4.0K  ~/projects/surakshit/          # community safety platform
drwxr-xr-x  omkar devops  4.0K  ~/projects/samku-cms/          # EV management system
drwxr-xr-x  omkar devops  4.0K  ~/projects/samku-services/     # vehicle service platform
```

<br/>

<div align="center">
<table>
<tr>
<td width="33%" valign="top">

**`./surakshit`** 🛡️
<br/>Community Safety Platform

`React` `Node.js` `Vercel`

[![Live](https://img.shields.io/badge/RUN-000000?style=for-the-badge&logo=vercel&logoColor=39FF14&labelColor=0D1117)](https://surakshit-three.vercel.app/)

</td>
<td width="33%" valign="top">

**`./samku-cms`** ⚡
<br/>EV Management System

`Full-Stack CMS` `Cloud`

[![Live](https://img.shields.io/badge/RUN-000000?style=for-the-badge&logo=vercel&logoColor=39FF14&labelColor=0D1117)](https://samku-cms.vercel.app)

</td>
<td width="33%" valign="top">

**`./samku-services`** 🚗
<br/>Vehicle Service Platform

`React` `Production`

[![Live](https://img.shields.io/badge/RUN-000000?style=for-the-badge&logo=vercel&logoColor=39FF14&labelColor=0D1117)](https://samkueservices.com)

</td>
</tr>
</table>
</div>

<br/>

<img src="https://capsule-render.vercel.app/api?type=rect&color=0:000000,100:0D1117&height=3&width=100%25" width="100%"/>

## `$` htop --stats github

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=dev-omkarbiradar&show_icons=true&theme=dark&hide_border=true&bg_color=000000&title_color=39FF14&icon_color=39FF14&text_color=C9D1D9&border_radius=8" height="165"/>
<img src="https://github-readme-streak-stats.herokuapp.com?user=dev-omkarbiradar&theme=dark&hide_border=true&background=000000&ring=39FF14&fire=39FF14&currStreakLabel=39FF14&border_radius=8" height="165"/>

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=dev-omkarbiradar&layout=compact&theme=dark&hide_border=true&bg_color=000000&title_color=39FF14&text_color=C9D1D9&border_radius=8" height="165"/>

<img src="https://github-profile-trophy.vercel.app/?username=dev-omkarbiradar&theme=onedark&no-frame=true&no-bg=true&row=1&column=6" width="90%"/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=dev-omkarbiradar&theme=github-dark&hide_border=true&bg_color=000000&color=39FF14&line=39FF14&point=FFFFFF&area=true&area_color=39FF14" width="90%"/>

</div>

<br/>

<div align="center">

### `$` cat contribution-grid.log

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/dev-omkarbiradar/dev-omkarbiradar/output/github-contribution-grid-snake-dark.svg">
  <img alt="snake animation" src="https://raw.githubusercontent.com/dev-omkarbiradar/dev-omkarbiradar/output/github-contribution-grid-snake.svg" width="90%">
</picture>

<sub>requires a one-time GitHub Actions workflow in this repo — ask and I'll generate it</sub>

</div>

<br/>

<div align="center">

<img src="https://komarev.com/ghpvc/?username=dev-omkarbiradar&style=for-the-badge&color=39FF14&label=PROFILE+VIEWS&labelColor=000000"/>

<br/><br/>

**`root@omkar-devops:~$` automate today, so tomorrow deploys itself.**

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:0D1117,100:000000&height=120&section=footer&text=omkar%40devops%3A~%24%20exit&fontColor=39FF14&fontSize=18&fontAlignY=75&animation=fadeIn" width="100%"/>

</div>
