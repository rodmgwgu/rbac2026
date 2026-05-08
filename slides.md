---
theme: ./theme
colorSchema: light
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
title: The Future of Roles & Permissions in Open edX
info: |
  ## The Future of Roles & Permissions in Open edX
  A Developer’s Guide to the New RBAC AuthZ System.

  by Rodrigo Mendez
drawings:
  persist: false
transition: slide-left
comark: true
duration: 30min
---

# The Future of Roles & Permissions in Open&nbsp;edX<sup>®</sup>

A Developer’s Guide to the New RBAC AuthZ System.

**Rodrigo Mendez** - Staff Software Engineer @ **WGU**

<div class="absolute bottom-32 right-8 flex flex-col items-end justify-end gap-4">
  <img src="/wgu-logo.png" class="h-24 box-content py-4" />
  <img src="/rgb-logo-open-edx-2026-horizontal.svg" class="h-24 box-content py-4" />
</div>



---
layout: two-cols
---

# Rodrigo Mendez

Staff Software Engineer

I'm a **software engineer**, hardware hobbyist and industrial design aficionado from Mexico.

I've been working with **Open edX** at **WGU** for over three years, where I've gained first-hand insight into the needs that large organizations have to better serve students.

I'm currently contributing to the Open edX project as a **Core Contributor** and maintainer of **openedx-authz**.

I've been tinkering with **Open Source Software** since **2006**.

::right::

<div class="flex flex-col items-center justify-center h-full">
  <img src="/contributors/rodmgwgu.jpeg" class="w-48 h-48 rounded-full object-cover" />
  <div class="flex flex-col gap-1 mt-4">
    <a href="https://github.com/rodmgwgu" target="_blank" class="flex items-center gap-2 text-sm">
      <carbon-logo-github /> rodmgwgu
    </a>
    <a href="https://github.com/rodmg" target="_blank" class="flex items-center gap-2 text-sm">
      <carbon-logo-github /> rodmg
    </a>
  </div>
</div>
---

# The Problem

No single authorization method in Open edX

- Libraries V2 - Custom model-based system (pre Ulmo)
- Course Authoring - A different model-based system
- LMS, Django, Forums, etc...

---

# Another Problem

Course Authoring: Hardcoded roles, tightly coupled with handler logic, not flexible enough.

Example: WGU required giving course author read-only permissions in studio.

- Users are authoring a course
- They want to use content from an existing course as reference
- They accidentaly make changes to the other course

More granular permissions would solve this issue.

---

# RBAC Project to the rescue

- Phase 1: Content Libraries (Ulmo)
- Phase 2: RBAC for Course Authoring (Verawood)

<br/>

## The RBAC Project is a collaboration between

<div class="grid grid-cols-4 gap-4 mt-4 items-center justify-center">
  <img src="/companies/edunext.svg" />
  <img src="/wgu-logo.png" />
  <img src="/companies/aulasneo.png" />
  <img src="/companies/axim.png" />
</div>

---

# The team

<div class="grid grid-cols-5 gap-4 mt-4">
  <div class="flex flex-col items-center">
    <img src="/contributors/mariajgrimaldi.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">mariajgrimaldi</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/mafermazu.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">MaferMazu</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/bryanttv.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">BryanttV</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/gviedma-aulasneo.png" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">Guillermo Viedma</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/mariadelosangeles.png" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">María de los Ángeles</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/bmtcril.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">bmtcril</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/rodmgwgu.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">rodmgwgu</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/wgu-taylor-payne.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">wgu-taylor-payne</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/dwong2708.png" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">dwong2708</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/dcoa.png" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">dcoa</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/jacobo-dominguez-wgu.png" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">jacobo-dominguez-wgu</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/jesusbalderramawgu.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">jesusbalderramawgu</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/bra-i-am.jpeg" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">bra-i-am</span>
  </div>
  <div class="flex flex-col items-center">
    <img src="/contributors/ccantillo.png" class="w-24 h-24 rounded-full object-cover" />
    <span class="text-xs mt-1">ccantillo</span>
  </div>
</div>

---

# Key Decisions

- Don't reinvent the wheel: Casbin
- Decouple roles and permissions from code
- Simple to understand even for non-technical users
- Single reusable library for the whole platform: openedx-authz
- Easy to use
- Simple extensibility (WIP)

<!--
Use industry standard technologies for authz.
 -->

---

# How

- Casbin, what is it, selection process
  - Talk about research and discussion done with the community
  - Talk about avoiding adding extra services

- Libraries (Ulmo)
- Course Authoring (Verawood)
- Next steps

---

# Casbin

Open-source authorizaton engine

A powerful and efficient open-source access control library that supports multiple authorization models

<div class="flex flex-col items-center justify-center h-100 pb-24">
  <img src="/casbin_logo.png" class="w-96" />
</div>

---
level: 2
---

# Casbin model

PERM metamodel: Policy, Effect, Request, Matchers

<div class="relative h-8">
  <div v-click-hide="1" class="absolute">Example Casbin model: <b>ACL</b></div>
  <div v-click="1" class="absolute">openedx-authz Casbin model: <b>RBAC</b></div>
</div>

````md magic-move {lines: true}
```ini
[request_definition]
r = sub, obj, act

[policy_definition]
p = sub, obj, act

[policy_effect]
e = some(where (p.eft == allow))

[matchers]
m = r.sub == p.sub && r.obj == p.obj && r.act == p.act

```

```ini
[request_definition]
r = sub, act, scope

[policy_definition]
p = sub, act, scope, eft

[role_definition]
g = _, _, _
g2 = _, _

[policy_effect]
e = some(where (p.eft == allow)) && !some(where (p.eft == deny))

[matchers]
m = is_staff_or_superuser(r.sub, r.act, r.scope) || (g(r.sub, p.sub, r.scope) || g(r.sub, p.sub, "*")) && 
    keyMatch(r.scope, p.scope) && (r.act == p.act || g2(p.act, r.act))
```
````
---
transition: fade
---

# Casbin policy

### <carbon-document /> Role definitions

|   | SUBJECT       | ACTION        | SCOPE | EFFECT |
|---|---------------|---------------|-------|--------|
| p | course_admin  | course.create | *     | ALLOW  |
| p | course_admin  | course.delete | *     | ALLOW  |
| p | course_admin  | course.view   | *     | ALLOW  |

### <carbon-data-base /> Role assignments

|   | USERNAME      | ROLE          | SCOPE                          |
|---|---------------|---------------|--------------------------------|
| g | johndoe       | course_admin  | course-v1:OpenedX+DemoX+2026   |
| g | aleidacortez  | course_admin  | course-v1:OpenedX+*            |

<!--
Casbin policies can be stored on file or DB

Currently, p role definitions are stored in a file on openedx-authz.

g (role assignations), are stored on DB
-->

---

# Casbin policy

### <carbon-data-base /> Role definition and assignments at runtime

|   | V0            | V1            | V2                             | V3    |
|---|---------------|---------------|--------------------------------|-------|
| p | course_admin  | course.create | *                              | ALLOW |
| p | course_admin  | course.delete | *                              | ALLOW |
| p | course_admin  | course.view   | *                              | ALLOW |
| g | johndoe       | course_admin  | course-v1:OpenedX+DemoX+2026   |       |
| g | aleidacortez  | course_admin  | course-v1:OpenedX+*            |       |



---

# References

- Understanding Casbin with different Access Control Model Configurations: https://articles.wesionary.team/understanding-casbin-with-different-access-control-model-configurations-faebc60f6da5
