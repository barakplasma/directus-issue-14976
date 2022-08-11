1. download https://github.com/lerocha/chinook-database/blob/e7e6d5f008e35d3f89d8b8a4f8d38e3bfa7e34bd/ChinookDatabase/DataSources/Chinook_Sqlite.sqlite
1. npm init directus-project issue-14976
1. configure with sqlite
1. change package json to "directus": "9.14.5",
1. delete data.db
1. move chinook into directory and change .env
1. npx directus bootstrap
1. npm install directus@latest
1. npm start

Logs
```sql
11:34:02 🔍 [0.127ms] select count(*) as `count` from `Album` limit ? [1]
11:34:02 ✨ request completed GET 304 /items/Album?limit=25&fields[]=AlbumId&fields[]=ArtistId&fields[]=Title&sort[]=AlbumId&page=1&meta[]=filter_count&meta[]=total_count 13ms
11:34:02 🔍 [0.646ms] select `ip_access` from `directus_roles` where `id` = ? limit ? [52a32391-0afe-4896-8e64-6da41c5b4dc6, 1]
11:34:02 🔍 [5.851ms] select `ip_access` from `directus_roles` where `id` = ? limit ? [52a32391-0afe-4896-8e64-6da41c5b4dc6, 1]
11:34:02 🔍 [4.259ms] select `directus_notifications`.`id`, `directus_notifications`.`subject`, `directus_notifications`.`collection`, `directus_notifications`.`item`, `directus_notifications`.`timestamp` from `directus_notifications` where (`directus_notifications`.`recipient` = ? and `directus_notifications`.`status` = ?) order by `directus_notifications`.`timestamp` desc limit ? [2eabedb4-8a81-4c48-8ce9-0772f68ddcad, inbox, 100]
11:34:02 ✨ request completed GET 304 /notifications?filter=%7B%22_and%22:[%7B%22recipient%22:%7B%22_eq%22:%222eabedb4-8a81-4c48-8ce9-0772f68ddcad%22%7D%7D,%7B%22status%22:%7B%22_eq%22:%22inbox%22%7D%7D]%7D&fields[]=id&fields[]=subject&fields[]=collection&fields[]=item&fields[]=timestamp&sort[]=-timestamp 15ms
11:34:02 🔍 [0.471ms] select `directus_settings`.`project_name`, `directus_settings`.`project_descriptor`, `directus_settings`.`project_logo`, `directus_settings`.`project_color`, `directus_settings`.`default_language`, `directus_settings`.`public_foreground`, `directus_settings`.`public_background`, `directus_settings`.`public_note`, `directus_settings`.`custom_css`, `directus_settings`.`id` from `directus_settings` order by `directus_settings`.`id` asc limit ? [1]
11:34:02 ✨ request completed GET 200 /server/info 15ms
```
1. npx directus database migrate:latest