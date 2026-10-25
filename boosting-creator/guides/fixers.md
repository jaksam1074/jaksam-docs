---
title: "Fixers"
description: "Boosting Creator fixers: named buyers who send contracts by email, ask for a clean car, a respray or tuning, and pay more as they trust the thief."
icon: "envelope"
---

A **fixer** is a named buyer. Instead of an anonymous offer, the player gets an email from them in the laptop, and after the job a reply in the **Inbox**. Fixers are on by default and set up in the **Fixers** tab of `/boostingcreator`.

## Fixer settings

| Field | What it does |
| --- | --- |
| **Name, initials, colour** | How the fixer appears in the emails. |
| **Classes** | The classes the fixer buys. |
| **Reputation required** | The fixer writes only to players with this reputation. |
| **Demand chance** | How often the fixer asks for something more. |
| **Demands** | Up to 10, see below. |
| **Messages** | The offer email, and the replies when the job went well, when a demand was missed and when it failed. |

Messages can use `{model}`, `{class}`, `{pay}`, `{colour}`, `{mods}`, `{condition}` and `{amount}`.

## Demands

A demand is an extra request on a drop-off contract:

| Type | The car must |
| --- | --- |
| **Clean** | Arrive with at least a given condition, for example 95 %. |
| **Respray** | Arrive in one of the chosen colours. It spawns in a very different colour, so it has to be painted. |
| **Tuning** | Have a number of upgrades among engine, brakes and transmission level 2 or more, turbo and xenon. |

Each demand has a **bonus** if met, a **penalty** if missed, **extra minutes** on the time limit, the **trust** it needs, and the number of **mechanics** that must be online (jobs set in **Settings > Contracts**). While driving, the objective card shows how far the car is from the demand, and turns green when it is met.

## Trust

Every character has a trust level from 0 to 100 with each fixer. Higher trust raises the pay, up to +20 % at full trust by default, and unlocks the demands that need it.

- A job done (with the demand met, or with no demand) adds trust.
- A missed demand takes some trust away.
- A failed or expired contract takes more.

The amounts are set in **Settings > Contracts**.

## The default fixers

| Fixer | Buys | From reputation | Asks for |
| --- | --- | --- | --- |
| Vinnie Russo | D to B | 0 | a clean car |
| Lola Navarro | C to S | 60 | a respray, with a mechanic online |
| Dmitri Volkov | B to S | 200 | tuning, and a very clean car once he trusts you |

<Info>
  With fixers off, or when no fixer buys the class, the offer is anonymous and has no demand.
</Info>
