# Project Version History - Wallet (Native Jetpack Compose)

## Libraries & Tools
- **Android Gradle Plugin (AGP):** 8.7.3
- **Kotlin:** 2.0.21
- **Compose Compiler Plugin:** 2.0.21
- **Compose BOM:** 2024.12.01
- **Material 3:** 1.3.1 (via BOM)
- **Material Icons Extended:** 1.7.6
- **Room Database:** 2.6.1 (with KSP)
- **Lifecycle Runtime & ViewModel Compose:** 2.8.7
- **Navigation Compose:** 2.8.5
- **Font Family:** Google Sans Flex (Offline bundled in `res/font/google_sans_flex.ttf`)

---

## [2026-09-06 21:00] - Initial Native Compose Core Architecture
- **Action:** Initial setup of Android Jetpack Compose native architecture.
- **Components:**
  - Room database (`WalletDatabase.kt`) with DAOs and entities for Accounts, Categories, Goals, Budgets, People, and Recurring Rules.
  - Unified Repository (`WalletRepository.kt`) providing reactive `Flow` data streams.
  - `WalletViewModel.kt` combining flows with `stateIn(WhileSubscribed(5000))`.
  - Material 3 theme system (`Theme.kt`, `Color.kt`, `PaletteStyle.kt`, `Type.kt`) supporting 10 dynamic palette styles and dark/light/AMOLED modes.
- **Status:** 100% (Core backend and data layer initialized).

## [2026-09-06 22:18] - Material 3 Expressive UI/UX Transformation
- **Action:** Major UI/UX overhaul to bring native Jetpack Compose Wallet on par with and exceeding the Wallet-Flutter Improv sandbox.
- **Architectural & Design Alignments:**
  - Strictly followed Material 3 Expressive design language and Native Android Mandate.
  - Utilized native Android primitives and Compose `Canvas` for custom visualizations (60-120 FPS hardware acceleration).
- **Files Created:**
  - `app/src/main/java/com/darkytm/wallet/ui/components/HomeHeader.kt`:
    - Contextual dynamic greeting (`Good Morning / Good Afternoon / Good Evening, User`) based on local time.
    - Glowing shadow vector logo mark.
    - Theme customizer trigger and interactive user profile avatar.
  - `app/src/main/java/com/darkytm/wallet/ui/components/AnimatedBalanceHero.kt`:
    - Material 3 Expressive card container (32dp rounded radius).
    - Native Compose `Canvas` organic background blobs (Primary & Tertiary radial gradients animated with `rememberInfiniteTransition` and ease loops).
    - Info dialog explaining net worth aggregation.
    - Eye visibility toggle button with obscured dot masking (`••••••••`).
    - "This month" spending percentage tag and dynamic `LinearProgressIndicator` shifting from primary to error red above 90% utilization.
    - Mini stat pills for Income (green trending up) and Expense (red trending down).
  - `app/src/main/java/com/darkytm/wallet/ui/components/OverviewGridSection.kt`:
    - 2-Column Expressive Grid with 8 Financial Hubs: Accounts, Budgets, Goals, Loans, Recurring, Categories, Bill Splitter, People.
    - Squircle icon containers with color tints, bold titles, real-time stat subtitles, and chevron navigation indicators.
  - `app/src/main/java/com/darkytm/wallet/ui/components/ActivityInsightsSection.kt`:
    - **Calendar Heatmap Card**: Month navigation (`< Month YYYY >`), weekday row (`M T W T F S S`), intensity-shaded day cells based on daily transaction totals, and interactive day detail chip.
    - **Activity Trends Card (30 days)**: Income & Expense summary badges, native Compose `Canvas` cubic bezier sparkline curve with vertical gradient fill and peak markers.
  - `app/src/main/java/com/darkytm/wallet/ui/components/RecentTransactionsSection.kt`:
    - Segmented filter control (`All`, `Expense`, `Income`, `Transfer`) with animated pill indicator.
    - Expressive transaction item rows with squircle category badges and relative timestamps (`Today`, `Yesterday`, or formatted date).
    - Interactive transaction detail modal bottom sheet with complete entity relations and deletion confirmation.
    - Stylized empty state with quick action button.
  - `app/src/main/java/com/darkytm/wallet/ui/components/OverviewDetailSheets.kt`:
    - Interactive modal bottom sheets for all 8 categories: Accounts list, Budgets progress list, Goals targets, Loans/Debts ledger, Recurring rules list, Categories list, Contacts list.
    - Fully interactive Bill Splitter calculator with tip percentage selector (0%, 10%, 15%, 20%) and people stepper (+ / -).
- **Files Modified:**
  - `app/src/main/java/com/darkytm/wallet/data/repository/WalletRepository.kt`:
    - Added `observeMonthlyStats()` flow calculating monthly income and monthly expense.
    - Added `MonthlyStats` data model.
  - `app/src/main/java/com/darkytm/wallet/ui/WalletViewModel.kt`:
    - Added `allTransactions`, `recurringRules`, `monthlyIncome`, `monthlyExpense`, and `isBalanceVisible` to `WalletUiState`.
    - Added `toggleBalanceVisibility()` and `addRecurringRule()`.
  - `app/src/main/java/com/darkytm/wallet/ui/screens/HomeScreen.kt`:
    - Replaced basic flat UI with the complete Material 3 Expressive experience integrating all 6 new modular components.
    - Preserved `ThemeCustomizerDialog` for dynamic theme/palette customization.
- **Status:** 100% (Complete, validated, and verified).

## [2026-09-06 22:22] - Transfer Account Routing & Input Refinement
- **Action:** Resolved destination account routing for transfers and refined input ergonomics.
- **Files Modified:**
  - `app/src/main/java/com/darkytm/wallet/ui/screens/AddEntryScreen.kt`:
    - Added `selectedToAccountId` state and dynamic destination account selection chips for `TransactionType.TRANSFER`.
    - Integrated `KeyboardType.Decimal` on the amount field to ensure proper numeric entry.
    - Added dedicated note input field.
    - Refined Material 3 Expressive input shapes, button styling, and layout spacing.
- **Status:** 100% (Complete, verified, ready for GitHub remote verification).

## [2026-09-19 21:32] - Official Vector Brand Logos & Profile Dialog Polish
- **Action:** Removed "Jetpack Compose" and "Material 3 Expressive" text descriptions from Profile & Settings dialog and replaced with authentic official vector logos.
- **Brand Vector Integration:**
  - Integrated official Android vector logo `app/src/main/res/drawable/ic_android_logo.xml` and official 22-path Jetpack Compose vector logo `app/src/main/res/drawable/ic_jetpack_compose_logo.xml`.
  - Replaced plain text with `Made with ❤️` and centered row `[Android Logo] ✕ [Jetpack Compose Logo]` with 70% opacity and `tint = Color.Unspecified`.
- **Files Created:**
  - `app/src/main/res/drawable/ic_android_logo.xml`
  - `app/src/main/res/drawable/ic_jetpack_compose_logo.xml`
- **Files Modified:**
  - `app/src/main/java/com/darkytm/wallet/ui/screens/HomeScreen.kt`
  - `Version.md`
- **Status:** 100% (Complete, verified, ready for GitHub remote verification).

## [2026-09-20 10:52] - Comprehensive README.md Documentation Synchronization
- **Action:** Synchronized `README.md` with all app features, architecture components, and design capabilities.
- **Documentation Highlights:**
  - Documented Animated Balance Hero with Compose `Canvas` organic gradient blobs, net worth insight dialog, eye balance toggle, and dynamic spending utilization indicator.
  - Documented 2-Column Expressive Grid detailing all 8 Financial Hubs (Accounts, Budgets, Goals, Loans/Debts, Recurring Rules, Categories, Interactive Bill Splitter, People/Contacts).
  - Documented Activity Insights section featuring the Calendar Heatmap with daily intensity shading and the 30-Day Activity Trends cubic bezier sparkline.
  - Documented Recent Transactions section with segmented filter pills, relative timestamps, and modal detail bottom sheets.
  - Documented transfer account routing with source/destination account chips.
  - Documented complete suite of 10 Material 3 Dynamic Palette styles, light/dark/AMOLED modes, offline Google Sans Flex variable font, and official Android & Jetpack Compose vector logos.
  - Updated architectural specifications table, project directory structure, and CI badges.
- **Files Modified:**
  - `README.md`
  - `Version.md`
- **Status:** 100% (Complete, verified, ready for GitHub remote verification).

## [2026-09-20 11:08] - Vector Drawable GitHub Pages Landing Deployment
- **Action:** Created dedicated GitHub Pages landing site in `docs/index.html` adopting the **Vector Drawable** dark Material 3 Expressive design language.
- **Components Featured:** Single Source of Truth architecture, Animated Balance Hero, 8 Financial Hubs, Calendar Heatmap, 30-Day Activity Trends, 10 M3 dynamic palettes, and offline Google Sans Flex variable font.
- **Files Created / Modified:**
  - `docs/index.html`
  - `Version.md`
- **Status:** 100% (Complete, verified, ready for GitHub remote verification).

## [2026-09-20 12:45] - Standardized Vector SVG Logo & GitHub Branding Integration
- **Action:** Standardized brand logo assets with crisp local vector `docs/logo.svg` across navbar toolbar and hero title heading.
- **Components Featured:**
  - Standardized brand logo display in navbar toolbar (40x40 container, 26x26 icon).
  - Integrated dedicated 64x64 squircle hero logo card alongside the page heading and title.
  - Added official GitHub SVG logos beside all GitHub mentions across navbar, action buttons, architectural specs, and footer.
- **Files Created / Modified:**
  - `docs/logo.svg`
  - `docs/index.html`
  - `Version.md`
- **Status:** 100% (Complete, verified, ready for GitHub remote verification).

## [2026-09-27 12:00:00 IST] - Codeberg Migration & Native Android Repository Setup
- **Action:** Configured secondary and primary mirror remotes for Codeberg (`codeberg.org/mrdarksidetm/Wallet`), validated SSH ED25519 signed commits, and configured Forgejo Actions workflow compatibility.
- **Changes:**
  - **Remote Architecture:** Added Codeberg Git remote `git@codeberg.org:mrdarksidetm/Wallet.git`.
  - **Cryptographic Signing:** Configured SSH commit signing with `id_ed25519_signing` for Codeberg verified commit status.
  - **CI/CD:** Prepared `.github/workflows/android-ci.yml` for Forgejo Actions execution.
- **Status:** 100% (Remote and cryptographic signing verified).

## [2026-10-01 12:38:00 IST] - GitHub junksidetm Setup & Tri-Platform Multi-Push Remote
- **Action**: Created new GitHub repository under `junksidetm/Wallet` and configured simultaneous multi-push synchronization across GitHub, GitLab, and Codeberg.
- **Changes**:
  - **Remote Architecture:** Configured `origin` remote to push concurrently to GitHub (`https://github.com/junksidetm/Wallet.git`), GitLab (`git@gitlab.com:mrdarksidetm/Wallet.git`), and Codeberg (`git@codeberg.org:mrdarksidetm/Wallet.git`).
  - **Credential & Identity Mapping:** Configured conditional Git identity (`.gitconfig-github`) utilizing `junksidetm <331540275+junksidetm@users.noreply.github.com>` for GitHub while maintaining `mrdarksidetm <ajukr99901@gmail.com>` for GitLab and Codeberg.
  - **Branch Synchronization:** Pushed `main` branch and tags to `junksidetm/Wallet`.
- **Status:** 100% (GitHub repository created, multi-push remote active, and branches synchronized across all 3 platforms).

## [2026-10-01 12:47:00 IST] - README Documentation GitHub Links Migration
- **Action**: Updated README.md documentation links, badges, and author references to point to active GitHub account `junksidetm` while preserving GitLab and Codeberg mappings.
- **Files Modified**:
  - `README.md`
  - `Version.md`
- **Status**: 100% (Completed & Synced)

## [2026-10-08 18:12:00 IST] - Tri-Platform Source Mirrors Integration
- **Action**: Added GitHub (Main), Codeberg (Mirror), and GitLab (Mirror) repository badges and dedicated Source Mirrors section in README.md.
- **Files Modified**:
  - `README.md`
  - `Version.md`
- **Status**: 100% (Completed & Synced)
