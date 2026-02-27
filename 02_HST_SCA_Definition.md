# 02_HST_SCA_Definition — HST に基づく SCA 構成の完全定義

**正本（Canonical）**: 日本語版。

本ドキュメントは、**HST (Holographic Sphere Topology)** に基づく **SCA（Software Composition Analysis / テックスタック構成分析）** の完全定義を提供する。Layered、Orthogonal、MECE の 3 原則を適用し、HST としての整合性を持ったデータ構造を定義する。

---

## 1. 軸の直交定義 (Orthogonal & HST Coordination)

各技術要素を以下の 3 つの独立した次元（Axis）で座標付けする。

| 軸 | 値 | 説明 |
|----|-----|------|
| **Layer (深度)** | `Core` / `Integration` / `Surface` | 内側から外側への距離。境界面からの距離 |
| **Aspect (断面/関心事)** | `Logic` / `UI` / `Storage` / `Network` / `Security` | 関心事の断面。HST の「点」の属性 |
| **Phase (時間軸/状態)** | `Build-time` / `Run-time` / `Managed-infra` | ライフサイクルフェーズ。Build-time は Manager 役、Run-time は Runtime 役 |

### 1.1 Layer の定義

| Layer | 説明 | 例 |
|-------|------|-----|
| **Core** | 系の中心。最も内側。データ・識別子・永続化 | SQLite, Drizzle, UUID |
| **Integration** | 臓器間の接続。境界面の Morphism | API 層、型・契約 |
| **Surface** | ユーザーが触れる境界面。事象の地平線 | SolidJS, Tailwind, https:// |

### 1.2 Aspect の定義

| Aspect | 説明 | 例 |
|--------|------|-----|
| **Logic** | ビジネスロジック・状態管理 | SolidJS Signals, 型定義 |
| **UI** | 表示・インタラクション | Tailwind, SolidJS コンポーネント |
| **Storage** | 永続化・貯蔵 | SQLite, Drizzle |
| **Network** | 通信・プロトコル | https://, PWA |
| **Security** | 認証・認可・境界 | Firebase Auth, ZKP |

### 1.3 Phase の定義

| Phase | 説明 | 例 |
|-------|------|-----|
| **Build-time** | ビルド・パッケージ管理 | Bun (Manager), Vite |
| **Run-time** | 実行時 | Bun (Runtime), SolidJS |
| **Managed-infra** | 外部管理インフラ | Firebase, サーバーレス |

---

## 2. MECE による多義性解消

### 2.1 重複排除（Normalization）

Bun のように役割が重複するものは、Phase 軸で `Build-time (Manager)` と `Run-time (Runtime)` に分離し、ID を一意に保ったまま多角的に参照できる構造とする。

| 技術 | Phase 分離 | ID |
|------|------------|-----|
| Bun | Build-time (Manager): パッケージ管理・ビルド / Run-time (Runtime): 実行エンジン | `bun-manager`, `bun-runtime` |

### 2.2 分解（Decomposition）

「Backend」や「Framework」といった曖昧なラベルを廃止し、HST の「点」として具体的なサービスに分解する。

| 曖昧ラベル | 分解後（HST の点） |
|-----------|-------------------|
| Backend | Firebase Auth, Drizzle, SQLite (LibSQL) |
| Framework | SolidJS, Tailwind CSS v4 |
| Runtime | Bun (Runtime) |

---

## 3. TypeScript Schema（Flat Data + Mapping）

```typescript
// ============================================================
// 軸の型定義
// ============================================================

export type Layer = 'Core' | 'Integration' | 'Surface';
export type Aspect = 'Logic' | 'UI' | 'Storage' | 'Network' | 'Security';
export type Phase = 'Build-time' | 'Run-time' | 'Managed-infra';

// ============================================================
// Flat Data: 各技術要素は 1 レコード。Nested Object は使わない
// ============================================================

export interface TechStackEntry {
  /** 一意 ID。Phase 分離時は bun-manager, bun-runtime のようにサフィックス */
  id: string;
  /** 表示名 */
  name: string;
  /** Layer: 内側から外側への深度 */
  layer: Layer;
  /** Aspect: 関心事の断面 */
  aspect: Aspect;
  /** Phase: ライフサイクル */
  phase: Phase;
  /** HST における役割（臓器メタファー） */
  hstRole?: string;
  /** 参照先 ID（Morphism の接続先）。境界面上の接続 */
  dependsOn?: string[];
}

// ============================================================
// Mapping: ID → Entry のマップ。正規化された参照用
// ============================================================

export type TechStackMap = Record<string, TechStackEntry>;

// ============================================================
// GAAS 標準スタックの例
// ============================================================

export const GAAS_STACK: TechStackEntry[] = [
  { id: 'sqlite-libsql', name: 'SQLite (LibSQL)', layer: 'Core', aspect: 'Storage', phase: 'Run-time', hstRole: '肝臓（DB）', dependsOn: [] },
  { id: 'drizzle', name: 'Drizzle ORM', layer: 'Core', aspect: 'Storage', phase: 'Run-time', hstRole: '型による境界面', dependsOn: ['sqlite-libsql'] },
  { id: 'solidjs', name: 'SolidJS', layer: 'Surface', aspect: 'Logic', phase: 'Run-time', hstRole: '境界面の振動（Signals）', dependsOn: [] },
  { id: 'tailwind-v4', name: 'Tailwind CSS v4', layer: 'Surface', aspect: 'UI', phase: 'Run-time', hstRole: '表面の模様', dependsOn: [] },
  { id: 'bun-manager', name: 'Bun (Manager)', layer: 'Integration', aspect: 'Logic', phase: 'Build-time', hstRole: '特異点・ビルド', dependsOn: [] },
  { id: 'bun-runtime', name: 'Bun (Runtime)', layer: 'Core', aspect: 'Logic', phase: 'Run-time', hstRole: '特異点・実行', dependsOn: [] },
  { id: 'https-pwa', name: 'https:// (PWA)', layer: 'Surface', aspect: 'Network', phase: 'Run-time', hstRole: '事象の地平線', dependsOn: [] },
];

// Flat Map への変換
export function toTechStackMap(entries: TechStackEntry[]): TechStackMap {
  return Object.fromEntries(entries.map((e) => [e.id, e]));
}
```

---

## 4. Topology View（ホログラフィック特性を維持するフィルタリング）

特定の Layer や Aspect でフィルタリングしても、システム全体の整合性が崩れない（Holographic な特性を維持する）ためのデータ抽出ロジック。

```typescript
// ============================================================
// Topology View: フィルタ後も依存関係を維持
// ============================================================

export interface TopologyFilter {
  layer?: Layer | Layer[];
  aspect?: Aspect | Aspect[];
  phase?: Phase | Phase[];
}

/**
 * フィルタを適用しつつ、dependsOn で参照されるエントリを
 * 再帰的に含める。境界面の整合性（ホログラフィック特性）を維持。
 */
export function filterTopology(
  map: TechStackMap,
  filter: TopologyFilter
): TechStackEntry[] {
  const layerSet = toSet(filter.layer);
  const aspectSet = toSet(filter.aspect);
  const phaseSet = toSet(filter.phase);

  const matches = (e: TechStackEntry): boolean => {
    if (layerSet && !layerSet.has(e.layer)) return false;
    if (aspectSet && !aspectSet.has(e.aspect)) return false;
    if (phaseSet && !phaseSet.has(e.phase)) return false;
    return true;
  };

  const resultIds = new Set<string>();

  const collect = (id: string) => {
    if (resultIds.has(id)) return;
    const entry = map[id];
    if (!entry) return;
    resultIds.add(id);
    // 依存先も再帰的に含める（境界面の接続を維持）
    entry.dependsOn?.forEach(collect);
  };

  // マッチするエントリとその依存先を再帰的に収集（境界面の整合性を維持）
  Object.values(map).filter(matches).forEach((e) => collect(e.id));

  return Array.from(resultIds)
    .map((id) => map[id])
    .filter((e): e is TechStackEntry => e != null);
}

function toSet<T>(v: T | T[] | undefined): Set<T> | null {
  if (v == null) return null;
  return new Set(Array.isArray(v) ? v : [v]);
}

// ============================================================
// 使用例
// ============================================================

// Surface 層のみ取得（Drizzle の依存先 SQLite も含まれる）
// const surfaceView = filterTopology(toTechStackMap(GAAS_STACK), { layer: 'Surface' });

// Logic 関心事のみ取得
// const logicView = filterTopology(toTechStackMap(GAAS_STACK), { aspect: 'Logic' });

// Build-time のみ取得
// const buildView = filterTopology(toTechStackMap(GAAS_STACK), { phase: 'Build-time' });
```

---

## 5. HST との対応

| HST 概念 | SCA 対応 |
|----------|----------|
| **Object（点）** | TechStackEntry。各技術は境界面上の点として一意に ID 付け |
| **Morphism（射）** | dependsOn。境界面を越える接続 |
| **境界面** | Layer=Surface のエントリ。ユーザーが触れる唯一の現実 |
| **臓器** | Aspect でグループ化された関心事の単位 |
| **トポロジー** | TechStackMap + filterTopology。フィルタ後も整合性を維持 |

---

## 6. 参照

- [00_HST_Basic_Concepts.md](00_HST_Basic_Concepts.md) — HST 基本概念
- [01_HST_IO_Specification.md](01_HST_IO_Specification.md) — I/O 仕様

---

## 更新履歴

| 日付 | 変更内容 |
|-----|----------|
| 2026-02-27 | 初版作成（Layered/Orthogonal/MECE、TypeScript Schema、Topology View） |
