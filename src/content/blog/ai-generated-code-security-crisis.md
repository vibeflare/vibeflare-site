---
title: "Why 45% of AI-Generated Code Fails Security Tests — and What to Do About It"
description: "Veracode's 2025 research tested 100+ LLMs and found nearly half of AI-generated code introduces OWASP Top 10 vulnerabilities. Here's what vibe coders need to know."
pubDate: 2025-02-21
author: "VibeFlare Team"
tags: ["security", "research", "OWASP"]
---

If you're building with Lovable, Cursor, Replit, or Bolt, your AI is writing code with a roughly 50/50 chance of introducing a security vulnerability. That's not speculation — it's the finding from Veracode's 2025 GenAI Code Security Report, the most comprehensive study of AI code security to date.

## What the research found

Veracode tested over 100 large language models across 80 code-completion tasks in Java, JavaScript, Python, and C#. When given a choice between a secure and insecure coding method, the models chose the insecure path 45% of the time.

The breakdowns are striking. Java had a 72% security failure rate — the highest of any language tested. Cross-site scripting defenses failed 86% of the time. Log injection defenses failed 88% of the time. SQL injection was the relative bright spot, with an 80% pass rate, as most modern LLMs default to parameterized queries.

Most importantly, security performance has remained flat even as AI models have gotten dramatically better at writing functional code. Newer, larger models don't produce meaningfully more secure code.

## What this means for vibe coders

If you're shipping a vibe-coded application with real users and real data, the odds are not in your favor. The vulnerabilities researchers are finding aren't theoretical — they're the kind that lead to data breaches, exposed user information, and regulatory headaches.

The most common patterns in vibe-coded apps include exposed Supabase service keys in frontend JavaScript bundles, Row-Level Security policies that exist but don't actually enforce access control, client-side-only authentication that can be bypassed by anyone with browser dev tools, and hardcoded secrets throughout the codebase.

## What you can do today

While you wait for better tooling (that's what we're building), there are immediate steps you can take. First, never put API keys or service-role keys in frontend code. If your AI put them there, move them to environment variables and a server-side function. Second, test your Supabase RLS policies manually — don't trust that they work just because they exist. Third, add server-side authentication checks. Client-side auth is a UX convenience, not a security boundary. Fourth, review what your application exposes publicly by opening your browser's Network tab and looking at what data comes back from your API calls.

Security doesn't have to slow you down. But ignoring it will catch up with you eventually — and the cost of a breach is always higher than the cost of prevention.
