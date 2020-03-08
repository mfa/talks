class: center, middle

# Git-annex -- lessons learned

Andreas Madsack (mfa)

datenobservatorium<br/>
2020-02-24

---

## Intro

- Michael introduced git-annex 4 weeks ago
- The purpose of git-annex is to backup and sync (big) files

---

## Problem: sync some images

- 2.3TB of images
- sync between home-server and internet-server
- not using the unitymedia uplink but the gbit uplink at work

---

## Solution: git annex

- git annex helps keeping partially checkouts
- but it has problems with lots of smalls files
- so, all images per folder are stored in one *tar* file now
- files for processing are extracted and shared with another server via sshfs

---

## Demo

---

## thanks

talk to me about

- python
- machine-learning
- computerlinguistics
