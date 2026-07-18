# SCBL dedicated server build status

- Result: **failure**
- Source commit: `f5793444d2184977a3570adca3c581311dece88a`
- Workflow run: `29655160671`
- Updated UTC: `2026-07-18T18:09:59Z`

| Step | Outcome |
|---|---|
| Dependencies | success |
| Rust toolchain | success |
| Formatting | failure |
| Tests | success |
| Release build | success |
| Artifact validation | success |
| GitHub Release | skipped |

## build.log

```text
   Compiling argh_derive v0.1.13
   Compiling color-eyre v0.6.5
   Compiling blake2 v0.11.0-rc.2
   Compiling sqlx-macros v0.8.6
   Compiling rust-fuzzy-search v0.1.1
   Compiling dedicated_server v0.2.5 (/home/runner/work/5th-echelon/5th-echelon/dedicated_server)
   Compiling argh v0.1.13
   Compiling argon2 v0.6.0-rc.1
   Compiling tonic-reflection v0.14.2
   Compiling tonic-async-interceptor v0.14.1
   Compiling sodiumoxide v0.2.7
   Compiling quazal v0.2.5 (/home/runner/work/5th-echelon/5th-echelon/quazal)
warning: unreachable expression
   --> quazal/src/rmc.rs:350:23
    |
350 |           let request = Request {
    |  _______________________^
351 | |             protocol_id: self.id(),
352 | |             method_id,
353 | |             parameters,
354 | |             call_id: todo!(),
    | |                      ------- any code following this expression is unreachable
355 | |         };
    | |_________^ unreachable expression
    |
    = note: `#[warn(unreachable_code)]` (part of `#[warn(unused)]`) on by default

warning: unreachable expression
   --> quazal/src/rmc.rs:360:66
    |
360 |         let _ = super::prudp::send_request(logger, ctx, todo!(), todo!(), req, ci);
    |                                                         -------  ^^^^^^^ unreachable expression
    |                                                         |
    |                                                         any code following this expression is unreachable
    |
    = note: this warning originates in the macro `todo` (in Nightly builds, run with -Z macro-backtrace for more info)

warning: unused variable: `logger`
   --> quazal/src/rmc.rs:349:20
    |
349 |     fn send(&self, logger: &Logger, ctx: &Context, ci: &mut ClientInfo<T>, method_id: u32, parameters: Vec<u8>) {
    |                    ^^^^^^ help: if this is intentional, prefix it with an underscore: `_logger`
    |
    = note: `#[warn(unused_variables)]` (part of `#[warn(unused)]`) on by default

warning: unused variable: `ctx`
   --> quazal/src/rmc.rs:349:37
    |
349 |     fn send(&self, logger: &Logger, ctx: &Context, ci: &mut ClientInfo<T>, method_id: u32, parameters: Vec<u8>) {
    |                                     ^^^ help: if this is intentional, prefix it with an underscore: `_ctx`

warning: unused variable: `ci`
   --> quazal/src/rmc.rs:349:52
    |
349 |     fn send(&self, logger: &Logger, ctx: &Context, ci: &mut ClientInfo<T>, method_id: u32, parameters: Vec<u8>) {
    |                                                    ^^ help: if this is intentional, prefix it with an underscore: `_ci`

warning: unused variable: `request`
   --> quazal/src/rmc.rs:350:13
    |
350 |         let request = Request {
    |             ^^^^^^^ help: if this is intentional, prefix it with an underscore: `_request`

warning: unused variable: `req`
   --> quazal/src/rmc.rs:356:13
    |
356 |         let req = QPacket {
    |             ^^^ help: if this is intentional, prefix it with an underscore: `_req`

warning: methods `calc_checksum` and `calc_signature` are never used
   --> quazal/src/prudp/packet.rs:311:19
    |
227 | impl QPacket {
    | ------------ methods in this implementation
...
311 |     pub(crate) fn calc_checksum(&self, ctx: &Context) -> u8 {
    |                   ^^^^^^^^^^^^^
...
317 |     pub(crate) fn calc_signature(&self, ctx: &Context, payload: &[u8]) -> u32 {
    |                   ^^^^^^^^^^^^^^
    |
    = note: `#[warn(dead_code)]` (part of `#[warn(unused)]`) on by default

   Compiling dedicated_server_config v0.2.5 (/home/runner/work/5th-echelon/5th-echelon/dedicated_server/config)
   Compiling sc_bl_protocols v0.2.5 (/home/runner/work/5th-echelon/5th-echelon/dedicated_server/sc_bl_protocols)
warning: `quazal` (lib) generated 8 warnings (run `cargo fix --lib -p quazal` to apply 5 suggestions)
   Compiling sqlx v0.8.6
warning: methods `register_user`, `find_user_by_ubi_id`, `find_user_by_id`, and `find_username_by_user_id` are never used
   --> dedicated_server/src/storage/mod.rs:90:12
    |
 33 | impl Storage {
    | ------------ methods in this implementation
...
 90 |     pub fn register_user(&self, username: &str, password: &str, ubi_id: Option<&str>) -> Result<()> {
    |            ^^^^^^^^^^^^^
...
121 |     pub fn find_user_by_ubi_id(&self, ubi_id: &str) -> Result<Option<User>> {
    |            ^^^^^^^^^^^^^^^^^^^
...
132 |     pub fn find_user_by_id(&self, id: u32) -> Result<Option<User>> {
    |            ^^^^^^^^^^^^^^^
...
164 |     pub fn find_username_by_user_id(&self, user_id: u32) -> Result<Option<String>> {
    |            ^^^^^^^^^^^^^^^^^^^^^^^^
    |
    = note: `#[warn(dead_code)]` (part of `#[warn(unused)]`) on by default

warning: field `receiver` is never read
   --> dedicated_server/src/storage/mod.rs:695:9
    |
692 | pub struct Invite {
    |            ------ field in this struct
...
695 |     pub receiver: u32,
    |         ^^^^^^^^
    |
    = note: `Invite` has a derived impl for the trait `Debug`, but this is intentionally ignored during dead code analysis

warning: `dedicated_server` (bin "dedicated_server") generated 2 warnings
    Finished `release` profile [optimized] target(s) in 3m 02s
```

## dependencies.log

```text
Get:1 file:/etc/apt/apt-mirrors.txt Mirrorlist [144 B]
Hit:6 https://packages.microsoft.com/repos/azure-cli noble InRelease
Hit:2 http://azure.archive.ubuntu.com/ubuntu noble InRelease
Get:7 https://packages.microsoft.com/ubuntu/24.04/prod noble InRelease [3600 B]
Get:3 http://azure.archive.ubuntu.com/ubuntu noble-updates InRelease [126 kB]
Get:4 http://azure.archive.ubuntu.com/ubuntu noble-backports InRelease [126 kB]
Get:5 http://azure.archive.ubuntu.com/ubuntu noble-security InRelease [126 kB]
Get:8 https://dl.google.com/linux/chrome-stable/deb stable InRelease [1825 B]
Get:9 https://packages.microsoft.com/ubuntu/24.04/prod noble/main amd64 Packages [231 kB]
Get:10 https://packages.microsoft.com/ubuntu/24.04/prod noble/main arm64 Packages [197 kB]
Get:11 https://packages.microsoft.com/ubuntu/24.04/prod noble/main armhf Packages [11.7 kB]
Get:12 http://azure.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages [1114 kB]
Get:13 http://azure.archive.ubuntu.com/ubuntu noble-updates/main Translation-en [272 kB]
Get:14 http://azure.archive.ubuntu.com/ubuntu noble-updates/main amd64 Components [180 kB]
Get:15 http://azure.archive.ubuntu.com/ubuntu noble-updates/universe amd64 Packages [1661 kB]
Get:16 http://azure.archive.ubuntu.com/ubuntu noble-updates/universe Translation-en [328 kB]
Get:17 http://azure.archive.ubuntu.com/ubuntu noble-updates/universe amd64 Components [389 kB]
Get:18 http://azure.archive.ubuntu.com/ubuntu noble-updates/restricted amd64 Packages [1256 kB]
Get:19 http://azure.archive.ubuntu.com/ubuntu noble-updates/restricted Translation-en [286 kB]
Get:20 http://azure.archive.ubuntu.com/ubuntu noble-updates/multiverse amd64 Components [940 B]
Get:21 http://azure.archive.ubuntu.com/ubuntu noble-backports/main amd64 Components [5744 B]
Get:22 http://azure.archive.ubuntu.com/ubuntu noble-backports/universe amd64 Components [10.5 kB]
Get:23 http://azure.archive.ubuntu.com/ubuntu noble-security/main amd64 Packages [853 kB]
Get:24 http://azure.archive.ubuntu.com/ubuntu noble-security/main Translation-en [191 kB]
Get:25 http://azure.archive.ubuntu.com/ubuntu noble-security/main amd64 Components [44.8 kB]
Get:26 http://azure.archive.ubuntu.com/ubuntu noble-security/universe amd64 Packages [1178 kB]
Get:27 http://azure.archive.ubuntu.com/ubuntu noble-security/universe Translation-en [232 kB]
Get:28 http://azure.archive.ubuntu.com/ubuntu noble-security/universe amd64 Components [76.2 kB]
Get:29 http://azure.archive.ubuntu.com/ubuntu noble-security/restricted amd64 Packages [1166 kB]
Get:30 http://azure.archive.ubuntu.com/ubuntu noble-security/restricted Translation-en [268 kB]
Get:31 https://dl.google.com/linux/chrome-stable/deb stable/main amd64 Packages [1223 B]
Fetched 10.3 MB in 1s (8478 kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
pkg-config is already the newest version (1.8.1-2build1).
libssl-dev is already the newest version (3.0.13-0ubuntu3.11).
libsqlite3-dev is already the newest version (3.45.1-1ubuntu2.6).
Suggested packages:
  protobuf-mode-el
The following NEW packages will be installed:
  build-essential libprotobuf-dev libprotobuf32t64 libprotoc32t64
  libsodium-dev protobuf-compiler
0 upgraded, 6 newly installed, 0 to remove and 24 not upgraded.
Need to get 3238 kB of archives.
After this operation, 18.6 MB of additional disk space will be used.
Get:1 file:/etc/apt/apt-mirrors.txt Mirrorlist [144 B]
Get:2 http://azure.archive.ubuntu.com/ubuntu noble/main amd64 build-essential amd64 12.10ubuntu1 [4928 B]
Get:3 http://azure.archive.ubuntu.com/ubuntu noble-updates/main amd64 libprotobuf32t64 amd64 3.21.12-8.2ubuntu0.3 [923 kB]
Get:4 http://azure.archive.ubuntu.com/ubuntu noble-updates/main amd64 libprotoc32t64 amd64 3.21.12-8.2ubuntu0.3 [683 kB]
Get:5 http://azure.archive.ubuntu.com/ubuntu noble-updates/main amd64 libsodium-dev amd64 1.0.18-1ubuntu0.24.04.1 [185 kB]
Get:6 http://azure.archive.ubuntu.com/ubuntu noble-updates/main amd64 libprotobuf-dev amd64 3.21.12-8.2ubuntu0.3 [1413 kB]
Get:7 http://azure.archive.ubuntu.com/ubuntu noble-updates/universe amd64 protobuf-compiler amd64 3.21.12-8.2ubuntu0.3 [29.0 kB]
Fetched 3238 kB in 1s (2682 kB/s)
Selecting previously unselected package build-essential.
(Reading database ... (Reading database ... 5%(Reading database ... 10%(Reading database ... 15%(Reading database ... 20%(Reading database ... 25%(Reading database ... 30%(Reading database ... 35%(Reading database ... 40%(Reading database ... 45%(Reading database ... 50%(Reading database ... 55%(Reading database ... 60%(Reading database ... 65%(Reading database ... 70%(Reading database ... 75%(Reading database ... 80%(Reading database ... 85%(Reading database ... 90%(Reading database ... 95%(Reading database ... 100%(Reading database ... 202507 files and directories currently installed.)
Preparing to unpack .../0-build-essential_12.10ubuntu1_amd64.deb ...
Unpacking build-essential (12.10ubuntu1) ...
Selecting previously unselected package libprotobuf32t64:amd64.
Preparing to unpack .../1-libprotobuf32t64_3.21.12-8.2ubuntu0.3_amd64.deb ...
Unpacking libprotobuf32t64:amd64 (3.21.12-8.2ubuntu0.3) ...
Selecting previously unselected package libprotoc32t64:amd64.
Preparing to unpack .../2-libprotoc32t64_3.21.12-8.2ubuntu0.3_amd64.deb ...
Unpacking libprotoc32t64:amd64 (3.21.12-8.2ubuntu0.3) ...
Selecting previously unselected package libsodium-dev:amd64.
Preparing to unpack .../3-libsodium-dev_1.0.18-1ubuntu0.24.04.1_amd64.deb ...
Unpacking libsodium-dev:amd64 (1.0.18-1ubuntu0.24.04.1) ...
Selecting previously unselected package libprotobuf-dev:amd64.
Preparing to unpack .../4-libprotobuf-dev_3.21.12-8.2ubuntu0.3_amd64.deb ...
Unpacking libprotobuf-dev:amd64 (3.21.12-8.2ubuntu0.3) ...
Selecting previously unselected package protobuf-compiler.
Preparing to unpack .../5-protobuf-compiler_3.21.12-8.2ubuntu0.3_amd64.deb ...
Unpacking protobuf-compiler (3.21.12-8.2ubuntu0.3) ...
Setting up libprotobuf32t64:amd64 (3.21.12-8.2ubuntu0.3) ...
Setting up libprotobuf-dev:amd64 (3.21.12-8.2ubuntu0.3) ...
Setting up libsodium-dev:amd64 (1.0.18-1ubuntu0.24.04.1) ...
Setting up build-essential (12.10ubuntu1) ...
Setting up libprotoc32t64:amd64 (3.21.12-8.2ubuntu0.3) ...
Setting up protobuf-compiler (3.21.12-8.2ubuntu0.3) ...
Processing triggers for man-db (2.12.0-4build2) ...
Not building database; man-db/auto-update is not 'true'.
Processing triggers for libc-bin (2.39-0ubuntu8.7) ...

Running kernel seems to be up-to-date.

No services need to be restarted.

No containers need to be restarted.

No user sessions are running outdated binaries.

No VM guests are running outdated hypervisor (qemu) binaries on this host.
```

## file.log

```text
dist/dedicated_server-linux-x86_64: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=e196c1253b1dbec02601f83a3bad766b0174e32d, stripped
```

## format.log

```text
+            self.storage
+                .leave_game_session(user_id, request.game_session_key.type_id, request.game_session_key.session_id,),
             logger,
             "error leaving game session"
         )?;
Diff in /home/runner/work/5th-echelon/5th-echelon/dedicated_server/src/game_session.rs:243:
         let user_id = login_required(&*ci)?;
         info!(logger, "Client abandons session: {:?}", request);
         rmc_err!(
-            self.storage.leave_game_session(
-                user_id,
-                request.game_session_key.type_id,
-                request.game_session_key.session_id,
-            ),
+            self.storage
+                .leave_game_session(user_id, request.game_session_key.type_id, request.game_session_key.session_id,),
             logger,
             "error abandoning game session"
         )?;
Diff in /home/runner/work/5th-echelon/5th-echelon/dedicated_server/src/game_session.rs:343:
         info!(logger, "Client migrates session host: {:?}", request);
 
         let migrated = rmc_err!(
-            self.storage.migrate_game_session_host(
-                user_id,
-                request.game_session_key.type_id,
-                request.game_session_key.session_id,
-            ),
+            self.storage
+                .migrate_game_session_host(user_id, request.game_session_key.type_id, request.game_session_key.session_id,),
             logger,
             "error migrating game session host"
         )?;
Diff in /home/runner/work/5th-echelon/5th-echelon/dedicated_server/src/overlord_core.rs:101:
             ("NC_CONNECTION_ESTABLISHED_TIMEOUT".to_owned(), F64(10.0)),
         ];
 
-                /*
+        /*
         // Alternative implementation using a HashMap for configuration values.
         // This could be used for more dynamic configuration loading.
          let cfg: std::collections::HashMap<std::string::String, Variant> = [
Diff in /home/runner/work/5th-echelon/5th-echelon/dedicated_server/src/overlord_news.rs:12:
 /// Represents a single news item.
 #[derive(Debug, ToStream, FromStream, Default, Deserialize)]
 struct NewsItem {
-    maybe_id: u32, // Likely a unique identifier for the news item.
-    unk2: u32,     // Unknown purpose.
-    unk3: u32,     // Unknown purpose.
-    unk4: u32,     // Unknown purpose.
-    unk5: String,  // Unknown purpose, possibly a category or source.
-    unk6: DateTime,// Unknown purpose, possibly creation or start date.
-    unk7: DateTime,// Unknown purpose, possibly an end date or last modified date.
+    maybe_id: u32,             // Likely a unique identifier for the news item.
+    unk2: u32,                 // Unknown purpose.
+    unk3: u32,                 // Unknown purpose.
+    unk4: u32,                 // Unknown purpose.
+    unk5: String,              // Unknown purpose, possibly a category or source.
+    unk6: DateTime,            // Unknown purpose, possibly creation or start date.
+    unk7: DateTime,            // Unknown purpose, possibly an end date or last modified date.
     expiration_time: DateTime, // The time when this news item expires.
-    title: String,       // The title of the news item.
-    link: String,        // A URL associated with the news item.
-    description: String, // The main content or description of the news item.
+    title: String,             // The title of the news item.
+    link: String,              // A URL associated with the news item.
+    description: String,       // The main content or description of the news item.
 }
 
 #[allow(clippy::module_name_repetitions)]
Diff in /home/runner/work/5th-echelon/5th-echelon/dedicated_server/src/storage/mod.rs:284:
             .execute(&mut *transaction)
             .await?;
 
-            let (participant_count,): (i64,) =
-                sqlx::query_as("SELECT COUNT(*) FROM participants WHERE game_id = ?")
-                    .bind(session_id)
-                    .fetch_one(&mut *transaction)
-                    .await?;
+            let (participant_count,): (i64,) = sqlx::query_as("SELECT COUNT(*) FROM participants WHERE game_id = ?")
+                .bind(session_id)
+                .fetch_one(&mut *transaction)
+                .await?;
 
             if participant_count == 0 {
                 sqlx::query(
Diff in /home/runner/work/5th-echelon/5th-echelon/dedicated_server/src/storage/mod.rs:389:
             .fetch_all(&self.pool))??
         } else {
             run(
-                sqlx::query_as(
-                    "SELECT type_id as session_type, id as session_id, creator_id, attributes FROM game_sessions WHERE type_id = ? AND destroyed_at IS NULL",
-                )
+                sqlx::query_as("SELECT type_id as session_type, id as session_id, creator_id, attributes FROM game_sessions WHERE type_id = ? AND destroyed_at IS NULL")
                     .bind(type_id)
                     .fetch_all(&self.pool),
             )??
Diff in /home/runner/work/5th-echelon/5th-echelon/quazal/src/prudp/packet.rs:185:
 #[derive(Debug, Copy, Clone)]
 pub enum PacketFlag {
     /// Acknowledgment flag.
-    Ack = 0b0001,      // 1
+    Ack = 0b0001, // 1
     /// Reliable delivery flag.
     Reliable = 0b0010, // 2
     /// Acknowledgment is required.
Diff in /home/runner/work/5th-echelon/5th-echelon/quazal/src/prudp/packet.rs:192:
-    NeedAck = 0b0100,  // 4
+    NeedAck = 0b0100, // 4
     /// The packet has a size field.
-    HasSize = 0b1000,  // 8
+    HasSize = 0b1000, // 8
 }
 
 /// Represents a PRUDP packet.
Diff in /home/runner/work/5th-echelon/5th-echelon/quazal/src/prudp/packet.rs:593:
         assert!(parse(ctx, &mut Cursor::new(data)).is_ok());
     }
 }
+
```

## rust-toolchain.log

```text
info: syncing channel updates for nightly-2025-10-15-x86_64-unknown-linux-gnu
info: latest update on 2025-10-15 for version 1.92.0-nightly (844264add 2025-10-14)
info: downloading 5 components

  nightly-2025-10-15-x86_64-unknown-linux-gnu installed - rustc 1.92.0-nightly (844264add 2025-10-14)

info: override toolchain for /home/runner/work/5th-echelon/5th-echelon set to nightly-2025-10-15-x86_64-unknown-linux-gnu
rustc 1.92.0-nightly (844264add 2025-10-14)
cargo 1.92.0-nightly (81c3f77a4 2025-10-10)
libprotoc 3.21.12
```

## tests.log

```text
    |
350 |           let request = Request {
    |  _______________________^
351 | |             protocol_id: self.id(),
352 | |             method_id,
353 | |             parameters,
354 | |             call_id: todo!(),
    | |                      ------- any code following this expression is unreachable
355 | |         };
    | |_________^ unreachable expression
    |
    = note: `#[warn(unreachable_code)]` (part of `#[warn(unused)]`) on by default

warning: unreachable expression
   --> quazal/src/rmc.rs:360:66
    |
360 |         let _ = super::prudp::send_request(logger, ctx, todo!(), todo!(), req, ci);
    |                                                         -------  ^^^^^^^ unreachable expression
    |                                                         |
    |                                                         any code following this expression is unreachable
    |
    = note: this warning originates in the macro `todo` (in Nightly builds, run with -Z macro-backtrace for more info)

warning: unused variable: `logger`
   --> quazal/src/rmc.rs:349:20
    |
349 |     fn send(&self, logger: &Logger, ctx: &Context, ci: &mut ClientInfo<T>, method_id: u32, parameters: Vec<u8>) {
    |                    ^^^^^^ help: if this is intentional, prefix it with an underscore: `_logger`
    |
    = note: `#[warn(unused_variables)]` (part of `#[warn(unused)]`) on by default

warning: unused variable: `ctx`
   --> quazal/src/rmc.rs:349:37
    |
349 |     fn send(&self, logger: &Logger, ctx: &Context, ci: &mut ClientInfo<T>, method_id: u32, parameters: Vec<u8>) {
    |                                     ^^^ help: if this is intentional, prefix it with an underscore: `_ctx`

warning: unused variable: `ci`
   --> quazal/src/rmc.rs:349:52
    |
349 |     fn send(&self, logger: &Logger, ctx: &Context, ci: &mut ClientInfo<T>, method_id: u32, parameters: Vec<u8>) {
    |                                                    ^^ help: if this is intentional, prefix it with an underscore: `_ci`

warning: unused variable: `request`
   --> quazal/src/rmc.rs:350:13
    |
350 |         let request = Request {
    |             ^^^^^^^ help: if this is intentional, prefix it with an underscore: `_request`

warning: unused variable: `req`
   --> quazal/src/rmc.rs:356:13
    |
356 |         let req = QPacket {
    |             ^^^ help: if this is intentional, prefix it with an underscore: `_req`

warning: methods `calc_checksum` and `calc_signature` are never used
   --> quazal/src/prudp/packet.rs:311:19
    |
227 | impl QPacket {
    | ------------ methods in this implementation
...
311 |     pub(crate) fn calc_checksum(&self, ctx: &Context) -> u8 {
    |                   ^^^^^^^^^^^^^
...
317 |     pub(crate) fn calc_signature(&self, ctx: &Context, payload: &[u8]) -> u32 {
    |                   ^^^^^^^^^^^^^^
    |
    = note: `#[warn(dead_code)]` (part of `#[warn(unused)]`) on by default

   Compiling dedicated_server_config v0.2.5 (/home/runner/work/5th-echelon/5th-echelon/dedicated_server/config)
   Compiling sc_bl_protocols v0.2.5 (/home/runner/work/5th-echelon/5th-echelon/dedicated_server/sc_bl_protocols)
warning: `quazal` (lib) generated 8 warnings (run `cargo fix --lib -p quazal` to apply 5 suggestions)
warning: methods `register_user`, `find_user_by_ubi_id`, `find_user_by_id`, and `find_username_by_user_id` are never used
   --> dedicated_server/src/storage/mod.rs:90:12
    |
 33 | impl Storage {
    | ------------ methods in this implementation
...
 90 |     pub fn register_user(&self, username: &str, password: &str, ubi_id: Option<&str>) -> Result<()> {
    |            ^^^^^^^^^^^^^
...
121 |     pub fn find_user_by_ubi_id(&self, ubi_id: &str) -> Result<Option<User>> {
    |            ^^^^^^^^^^^^^^^^^^^
...
132 |     pub fn find_user_by_id(&self, id: u32) -> Result<Option<User>> {
    |            ^^^^^^^^^^^^^^^
...
164 |     pub fn find_username_by_user_id(&self, user_id: u32) -> Result<Option<String>> {
    |            ^^^^^^^^^^^^^^^^^^^^^^^^
    |
    = note: `#[warn(dead_code)]` (part of `#[warn(unused)]`) on by default

warning: field `receiver` is never read
   --> dedicated_server/src/storage/mod.rs:695:9
    |
692 | pub struct Invite {
    |            ------ field in this struct
...
695 |     pub receiver: u32,
    |         ^^^^^^^^
    |
    = note: `Invite` has a derived impl for the trait `Debug`, but this is intentionally ignored during dead code analysis

warning: `dedicated_server` (bin "dedicated_server" test) generated 2 warnings
    Finished `test` profile [unoptimized + debuginfo] target(s) in 1m 42s
     Running unittests src/bin/cli.rs (target/debug/deps/cli-7a15a53dad806cb0)

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out; finished in 0.00s

     Running unittests src/main.rs (target/debug/deps/dedicated_server-e1f9af9b90806e8d)

running 3 tests
test overlord_challenge::tests::parse_sample ... ok
test overlord_core::tests::test_method1 ... ok
test overlord_news::tests::parse_sample ... ok

test result: ok. 3 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out; finished in 0.00s

```

