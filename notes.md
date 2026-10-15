# Offline Study — Project Notes

An Android app that saves web content for offline reading.
Long-term goal: an offline mini-internet for students.

---

## Session Log

### 2026-10-15 — First working version

**Built:**
- First Compose screen: URL input + Save button
- Room database for storing saved URLs
- Add / list / delete saved articles
- Persistence across app restarts (verified)

**Learned:**
- Write → Build → Run loop in Android Studio
- How Compose describes UI in Kotlin code
- How Room stores data on disk (Entity, DAO, Database)
- How a ViewModel connects the UI to the database
- How Git commits create restore points

**Known issues:**
- No URL validation — typing "hello" saves it as a URL
- Title extraction is crude: `url.substringAfter("://").substringBefore("/")`
- No tapping a card to open anything yet — cards are display-only

**Next session:**
- Fetch page HTML with OkHttp when a card is tapped
- Store HTML + assets locally
- Display in a WebView (offline)
- Fix URL validation while building this

---

## Project State

**Package:** `com.alex.offlinestudy`
**Min SDK:** 24
**Language:** Kotlin
**UI:** Jetpack Compose (Material 3)

**Stack:**
- Kotlin 2.2.10
- Jetpack Compose (BOM 2026.02.01)
- Room 2.8.1 (via KSP)
- Lifecycle ViewModel Compose 2.8.7
- AGP 9.4.1

**Files:**
| File | Purpose |
|------|---------|
| `MainActivity.kt` | Main screen + LibraryViewModel (add/remove/list) |
| `SavedArticle.kt` | Room entity: id, url, title, savedAt |
| `SavedArticleDao.kt` | Room DAO: insert, delete, getAll (Flow) |
| `AppDatabase.kt` | Room database singleton |

**Database schema:**
