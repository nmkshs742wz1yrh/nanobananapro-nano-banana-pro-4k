# gemini-3-pro-image-preview API (nanobananapro) — 4K guide with per-unit pricing

<p align="center">
  <img src="assets/hero.jpg" width="820" alt="gemini-3-pro-image-preview sample">
</p>

> **4K at $0.04 per image** (default $0.03) — up to 14 reference images, flat per-image billing.

**[Model page](https://apimart.ai/model/gemini-3-pro-image-preview)** · **[Live pricing](https://apimart.ai/pricing)** · **[Get an API key](https://apimart.ai/keys)**

Everything on this page refers to **gemini-3-pro-image-preview** — also written **nanobananapro**, **gemini 3 pro image preview** or **gemini-3-pro-image-preview** — served through the OpenAI-compatible APIMart gateway at `https://api.apimart.ai/v1`.

## Pricing (observed, snapshot 2026-09-24)

| Tier | Price |
| --- | --- |
| `4K` | $0.04 |
| `default` | $0.03 |

Billed per unit, pay as you go, **$1 minimum top-up**, no subscription and no free quota. Every task response returns `cost` / `credits_cost` so the charge can be checked per call.

## What that costs at scale

| Volume | Cost |
| --- | --- |
| 100 | $3 |
| 1000 | $30 |

Linear at the observed rate, no volume discount assumed.

## How to call it

```bash
export APIMART_API_KEY="<token>"
curl --request POST --url https://api.apimart.ai/v1/images/generations \
  --header "Authorization: Bearer $APIMART_API_KEY" --header 'Content-Type: application/json' \
  --data '{"model":"gemini-3-pro-image-preview","prompt":"a modern cliffside villa at dusk, slow camera push","size":"16:9","n":1}'
```

Submit, keep the `task_id`, then poll `GET /v1/tasks/{id}` until `completed`. The response carries the image/video URL and the exact amount charged.

## Troubleshooting the first call

| Symptom | Cause | Fix |
| --- | --- | --- |
| `401` | key missing or truncated | re-copy from the console; header is `Authorization: Bearer $APIMART_API_KEY` |
| no balance | account has no credit | top up from $1 — there is no free tier on any model here |
| `429` | too many concurrent calls on one key | back off, retry with the same `Idempotency-Key` |
| `model` not found | wrong id or wrong tier field | copy the exact id `gemini-3-pro-image-preview` (alias `nanobananapro`) from the table above |
| task `failed` | prompt filtered, or a reference URL expired | resubmit with a new `Idempotency-Key` |

## FAQ

**How is it billed?** Per delivered image, by resolution tier.
**Which resolutions?** 4K, default.
**Is this a relay?** Yes — APIMart is a third-party gateway. Same OpenAI-compatible request shape, different billing and settlement from the vendor's direct API.

## Disclosure

This repository documents access through APIMart, a third-party API gateway, and is not affiliated with the model vendor. Prices are the dated snapshot above; the platform console is authoritative for billing.
