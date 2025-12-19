# Changelog

All notable changes to this project are recorded here.

## Unreleased

- Added: Mouse click/drag selection (left-click places caret | drag selects text). This feature
  required changes to the annotation/highlighter pipeline and revealed a bug where annotations
  used byte indices that could slice inside multi-byte grapheme clusters (for example, emoji
  using ZWJ sequences), causing panics when rendering or iterating annotated strings.
- Fixed: Introduced grapheme-aware helpers and converted grapheme indices to safe byte offsets
  before annotating and slicing. This prevents invalid byte-slicing and crashes when search
  query matches include multi-byte grapheme clusters.
- Internal: Selection rendering implemented via `AnnotationType::SelectedMatch`; mouse routing
  and handling added. See `src/editor/uicomponents/view/mod.rs`, `src/editor/annotatedstring/mod.rs`,
  and `src/editor/line/mod.rs` for details.
