# Constantine Yachts — DB Backups

Otomatik DB yedekleri. Her gece 03:00'te `scripts/backup.mjs` tarafından oluşturulur, buraya push edilir.

**Bu repo PRIVATE olmalı** — yedek dosyaları müşteri/booking bilgisi içerir.

## Restore

Yedeği geri yüklemek için Constantine projesinde:

```bash
# Önce dosyayı buradan çek
cd C:\Users\aziz_\OneDrive\Constantine-Backups
git pull

# Constantine'de restore et
cd C:\Users\aziz_\Downloads\constantine
node --env-file=.env.local scripts/restore.mjs backups/backup-YYYY-MM-DD....json.gz --dry-run
node --env-file=.env.local scripts/restore.mjs backups/backup-YYYY-MM-DD....json.gz --table=bookings --confirm
```

## Yedek formatı

- `backup-YYYY-MM-DDTHH-MM-SS.json.gz` — gzip JSON
- 23 tablo: profiles, channels, packages, products, boats, bookings, expenses, tasks, channel_settlements, vd.
