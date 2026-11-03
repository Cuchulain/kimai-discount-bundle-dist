# Kimai DiscountBundle – downloads

Discounts on individual [Kimai](https://www.kimai.org) invoices: fixed amounts or percentages, applied before tax,
with correct totals on the invoice, in the invoice history and in the report "Invoiced (with discounts)".

This repository only hosts the released plugin packages. The source code is not public.

## Download

**Latest version:** [DiscountBundle.zip](https://github.com/Cuchulain/kimai-discount-bundle-dist/releases/latest/download/DiscountBundle.zip)

All versions and changes: [Releases](https://github.com/Cuchulain/kimai-discount-bundle-dist/releases)

## Installation

Requires Kimai 2.71 or newer.

```bash
cd /path/to/kimai
unzip DiscountBundle.zip -d var/plugins/     # creates var/plugins/DiscountBundle/
bin/console kimai:reload
bin/console kimai:bundle:discount:install
```

Run the commands as the web server user (e.g. `sudo -u www-data`). Updates: replace the directory
`var/plugins/DiscountBundle/` and run the same commands. Detailed documentation (Czech) is in `README.md` inside the ZIP.

## Setup

1. **Choose a discount calculator** in **Invoices → Invoice template → (edit) → Grouping of invoice lines**:
   - "Default (one row per entry) + discount" (instead of Kimai's "Default"), or
   - "Project + discount" (instead of "Project").

   Discounts work only with invoice templates using one of these calculators. With any other calculator Kimai
   rejects the invoice preview and saving with a discount, a discount is never ignored silently.
2. **Enter a discount** on **Invoices → Create invoice**: click **+ Discount** in the customer row, add one or more
   lines (fixed net amount or percentage) and click **Use**. The total column shows the discounted total right away.
   Preview the invoice as often as you like; saving the invoice uses the discount, exactly once.
   All discounts are listed under **Invoices → Invoice discounts**.

Discounts are applied one after another on the remaining net amount, then the tax is calculated:
1,000 − 10 % − 100 = 800 net, 968 with 21 % VAT.

### Invoice documents

No changes are needed in the invoice document (`.twig`): discounts are regular invoice lines with a negative amount,
and `invoice.subtotal`, `invoice.tax_rows`, `invoice.total` already include them. Kimai's built-in documents work
as they are. Never subtract the discount again in a template.

Only custom documents that calculate totals on their own from the time entries need an update. Optional variables:

| Variable | Meaning |
| --- | --- |
| `entry['entry.discount']` | `true` for a discount line |
| `entry['entry.discount_type']`, `entry['entry.discount_value']` | `percent` / `fixed` and the entered value |
| `invoice['invoice.discount_applied']` | whether the invoice has a discount |
| `invoice['invoice.discount_total']`, `..._plain` | total discount (formatted / number) |
| `invoice['invoice.subtotal_before_discount']`, `..._plain` | net amount before the discount |

## Free version and license

- Free: 3 discounts per month, all invoice features.
- License (49 € / year): unlimited discounts and the report "Invoiced (with discounts)",
  [buy on Lemon Squeezy](https://witcher.lemonsqueezy.com/checkout/buy/a7fea23c-0c89-49e4-8d8a-71d21d94d8ed).
  Activate it in Kimai under **System → DiscountBundle license**.

The plugin is proprietary software, see [LICENSE](LICENSE).
