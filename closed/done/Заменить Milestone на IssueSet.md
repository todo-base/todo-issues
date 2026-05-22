---
assignee: XX
status: done
---

# Заменить Milestone на IssueSet

Сейчас в markdown-файле список issues могут дополнять milestones, которые выглядят как заголовки разделов. Необходимо избавиться от milestones в пользу организации issues в наборы (IssueSet), если в markdown-файле они идут в одном разделе с заголовком. При этом сам заголовок будет являться именем набора.  

Структура
```rust
pub struct Milestone<ID> {
    pub id: ID,
    pub name: String,
    pub needed_issues: IndexSet<ID>,
}
```
Преобразуется в структуру вида
```rust
pub struct IssueSet {
    pub name: String,
    pub issues: IndexSet<ID>,
}
```
В случае иерерхии заголовков, имя набора формируется как уникальный путь `parent name/set name`.

Нужно внести исправление в код и добавить новые test-cases в тесты `cli/tests`.
