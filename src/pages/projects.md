---
title: Projects
display: Projects
wrapperClass: 'text-center'
projects:
  Vue Component:
    - name: 'NaiveChat'
      link: 'https://github.com/kinggq/naive-chat'
      desc: '基于Vue3的聊天组件，支持Typescript'
      icon: 'i-material-symbols:android-chat'
    - name: 'ScheduleVue'
      link: 'https://github.com/kinggq/vue-schedule'
      desc: '基于Vue3 Typescript的时间表拖拽选择组件，例如广告投放时间排期选择等。'
      icon: 'i-arcticons:betterschedule'
    - name: 'Whiteboard'
      link: 'https://github.com/kinggq/whiteboard'
      desc: '基于Vue3 Typescript的时间表拖拽选择组件，例如广告投放时间排期选择等。'
      icon: 'i-vscode-icons:file-type-taskfile'
---

<!-- @layout-full-width -->

<ListProjects :projects="frontmatter.projects" />
