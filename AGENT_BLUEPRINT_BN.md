# ফুল-স্ট্যাক Advertising AI Agent (No API Cost যতটা সম্ভব)

## 1) বাস্তবতা আগে (খুব গুরুত্বপূর্ণ)
- **১০০% no-cost + ১০০% perfect + পুরো কোম্পানি auto-run** বাস্তবে সম্ভব না।
- তবে **নিজের লোকাল মেশিনে ওপেন-সোর্স মডেল** (যেমন Ollama) চালিয়ে, workflow automation, human approval gate, এবং ads platform API দিয়ে খুব শক্তিশালী সিস্টেম বানানো সম্ভব।
- লক্ষ্য হবে: **human-in-the-loop autopilot** (আপনি final approve করবেন, সিস্টেম বাকি কাজ করবে)।

## 2) কী কী কাজ agent করবে
এই agent আপনার দেয়া requirement অনুযায়ী end-to-end কাজ ভাগ করে করবে:
1. Planning & Strategy
2. Campaign Structure
3. SEO/SEM keyword research
4. High-conversion ad copy
5. Funnel-wise campaign creation
6. Account audit
7. Audit-driven optimization
8. Google Ads conversion tracking setup
9. সব ad platform conversion/pixel/CAPI setup checklist
10. Data analysis + report (PDF/TXT/JSON)
11. Live step-by-step activity feed
12. Local folder এ সব artifact save

## 3) প্রস্তাবিত আর্কিটেকচার
### Core components
- **Coordinator Agent**: user requirement নেয়, task breakdown করে
- **Specialist Agents**:
  - Strategy Agent
  - Keyword Agent
  - Copy Agent
  - Tracking Agent
  - Audit Agent
  - Reporting Agent
- **Approval Gateway**: client এ পাঠানোর আগে আপনার approval নেয়
- **Action Runner**:
  - API connectors (Google Ads, GA4, Meta, TikTok)
  - Browser automation (Playwright) for guided/manual fallback
- **State + Memory**:
  - SQLite/Postgres for job state
  - Vector memory (optional) for client history
- **Artifact Store**:
  - `/workspace/clients/<client_id>/...` এ JSON/TXT/PDF

## 4) নিরাপত্তা (মাস্ট)
- OAuth only (plain password store না)
- Secret manager (env vault)
- Role-based access
- Every action log + reversible change পরিকল্পনা
- Destructive change এর আগে mandatory approval

## 5) Recommended stack (low/no API cost)
- **LLM runtime:** Ollama (Llama 3.1 / Qwen / Mistral)
- **Orchestration:** Python + FastAPI
- **Automation:** Playwright
- **Scheduler:** Celery বা APScheduler
- **Database:** SQLite (start) → Postgres (scale)
- **Reporting:** Pandas + Matplotlib + WeasyPrint/ReportLab
- **UI:** Next.js বা Streamlit (live steps, approvals)

## 6) Workflow (step-by-step)
1. আপনি requirement দেন
2. Agent required access checklist তৈরি করে
3. Agent access request করে (once)
4. Discovery scan: account/campaign/audience/asset
5. Strategy draft + campaign map
6. Keyword clusters + ad groups
7. Ad copy variants (TOFU/MOFU/BOFU)
8. Tracking design (events, UTM, GA4, conversions)
9. Implementation plan + risk note
10. **আপনার approval**
11. API/Automation execution
12. QA checks (event fire, conversion import, spend guardrails)
13. Daily optimization loop
14. Client-ready report + sample creatives + next actions

## 7) Folder structure (local)
```text
agent-system/
  app/
    main.py
    orchestrator/
    agents/
    connectors/
    automation/
    reporting/
  data/
    clients/
      <client_id>/
        briefs/
        audits/
        campaigns/
        tracking/
        reports/
        logs/
  configs/
  .env
```

## 8) JSON outputs (example)
- `campaign_plan.json`
- `keyword_research.json`
- `ad_copy_variants.json`
- `tracking_map.json`
- `audit_report.json`
- `optimization_actions.json`
- `execution_log.json`

## 9) “No issue” delivery design
- Preflight validator (budget, geo, conversion action match)
- Simulation mode (dry run)
- Rollback snapshot
- Human approval বাধ্যতামূলক stage
- Regression checklist before “Done”

## 10) MVP plan (14 দিন)
- Day 1-2: Auth + project skeleton
- Day 3-4: Requirement ইনটেক + planning agent
- Day 5-6: Keyword + copy modules
- Day 7-8: Google Ads + GA4 conversion connector
- Day 9-10: Meta pixel/CAPI guided setup module
- Day 11: Audit + optimization rule engine
- Day 12: Live activity dashboard
- Day 13: PDF/TXT রিপোর্ট জেনারেটর
- Day 14: QA + hardening

## 11) Limitations (clear expectation)
- কিছু platform action human approval বা manual 2FA লাগতে পারে
- UI changes হলে browser automation ভাঙতে পারে
- “পুরোপুরি autonomous” না করে “supervised autonomy” সবচেয়ে safe

## 12) Next step (আমি এখনই build শুরু করতে পারি)
আপনি চাইলে পরের ধাপে আমি:
1. পূর্ণ codebase scaffold তৈরি করব
2. Local run instructions দেব
3. Sample client workflow দিয়ে end-to-end demo artifacts generate করব

