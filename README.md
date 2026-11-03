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

## Free version and license

- Free: 3 discounts per month, all invoice features.
- License (49 € / year): unlimited discounts and the report "Invoiced (with discounts)",
  [buy on Lemon Squeezy](https://witcher.lemonsqueezy.com/checkout/buy/a7fea23c-0c89-49e4-8d8a-71d21d94d8ed).
  Activate it in Kimai under **System → DiscountBundle license**.

The plugin is proprietary software, see [LICENSE](LICENSE).
