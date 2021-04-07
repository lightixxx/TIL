# scss-lint
코드를 일관성있게 작성할 수 있도록 도와주는 녀석이다. 문법적인 실수, 정해놓은 규칙에서 어긋났을 때 자동으로 고쳐준다.

> 협업을 하게되면 linter가 얼마나 중요한지 알게될 것이다!

<br />

## 사용법

root에 .scss-lint.yml 파일을 생성한다.
```yml
scss_files: '**/*.scss'

severity: warning

linters:
  BorderZero:
    enabled: true
    convention: zero

  ColorKeyword:
    enabled: true

  ColorVariable:
    enabled: false

  Comment:
    enabled: false
    style: silent

  DeclarationOrder:
    enabled: false

  DisableLinterReason:
    enabled: false

  DuplicateProperty:
    enabled: true

  EmptyLineBetweenBlocks:
    enabled: true
    ignore_single_line_blocks: true

  EmptyRule:
    enabled: true

  ExtendDirective:
    enabled: false

  FinalNewline:
    enabled: true
    present: true

  HexLength:
    enabled: true
    style: short

  HexNotation:
    enabled: true
    style: lowercase

  HexValidation:
    enabled: true

  IdSelector:
    enabled: false

  ImportantRule:
    enabled: false

  ImportPath:
    enabled: true
    leading_underscore: false
    filename_extension: false

  Indentation:
    enabled: true
    allow_non_nested_indentation: false
    character: space
    width: 2

  LeadingZero:
    enabled: true
    style: include_zero

  MergeableSelector:
    enabled: true
    force_nesting: true

  NestingDepth:
    enabled: true
    max_depth: 6
    ignore_parent_selectors: false

  PlaceholderInExtend:
    enabled: true

  PrivateNamingConvention:
    enabled: false
    prefix: _

  PropertySortOrder:
    enabled: true
    order: recess
    ignore_unspecified: false
    min_properties: 2
    separate_groups: false

  PropertySpelling:
    enabled: true
    extra_properties: []
    disabled_properties: []

  PseudoElement:
    enabled: true

  QualifyingElement:
    enabled: true
    allow_element_with_attribute: false
    allow_element_with_class: false
    allow_element_with_id: false

  SelectorDepth:
    enabled: true
    max_depth: 6

  SelectorFormat:
    enabled: false

  Shorthand:
    enabled: false
    allowed_shorthands: [1, 2, 3, 4]

  SingleLinePerProperty:
    enabled: true
    allow_single_line_rule_sets: true

  SingleLinePerSelector:
    enabled: true

  SpaceAfterComma:
    enabled: true
    style: one_space

  SpaceAfterComment:
    enabled: false
    style: one_space

  SpaceAfterPropertyName:
    enabled: true

  SpaceAfterVariableName:
    enabled: true

  SpaceAroundOperator:
    enabled: true
    style: one_space

  SpaceBeforeBrace:
    enabled: true
    style: space
    allow_single_line_padding: false

  SpaceBetweenParens:
    enabled: true
    spaces: 0

  StringQuotes:
    enabled: true
    style: single_quotes

  TrailingSemicolon:
    enabled: true

  TrailingWhitespace:
    enabled: true

  TrailingZero:
    enabled: false

  UnnecessaryParentReference:
    enabled: true

  UrlFormat:
    enabled: true

  UrlQuotes:
    enabled: true

  VariableForProperty:
    enabled: false
    properties: []

  VendorPrefix:
    enabled: true
    identifier_list: base
    additional_identifiers: []
    excluded_identifiers: []

  ZeroUnit:
    enabled: true
```