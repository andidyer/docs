---
layout: base
title:  'Bengali UD'
udver: '2'
---

# UD for Bengali <span class="flagspan"><img class="flag" src="../../flags/svg/BD.svg" /></span> <span class="flagspan" style="padding-left:1em"><img class="flag" src="../../flags/svg/IN.svg" /></span>

## Tokenization and Word Segmentation

* In general, words are delimited by whitespace characters. Description of exceptions follows.
* According to typographical rules, some punctuation marks (e.g., comma) are attached to a neighboring word,
  while others (e.g., the sentence-terminating danda) are not.
  We tokenize punctuation as separate tokens (words).
* Multiword tokens (MWTs) are possible in Bengali, with the following as examples:
  * Contractions of a finite verb and a negative adverb, e.g. করেনি _koreni_ ("did not do"), 
    where করে and নি are the components, with the lemma কর and না respectively.
  * Numeral classifier expressions such as দুইজন _duljon_ ("two person.CLF"), formed from দুই _dul_ and জন _jon_.

## Morphology

### Tags

* Bengali uses all 17 universal POS categories, including particles ([PART]()).
* The following words are classified as particles ([PART]()):
  * না _nā_, নাই _nāi_ the negative particle (“not”).
  * কি _ki_ when it functions as a question particle (rather than the pronoun “what”) that marks a yes-no question.
* At present, only some modal verbs are treated as auxiliaries ([AUX]()):
  * পারা _pārā_ (“be able, can, could”) combines with the imperfect participle (also called the infinitive) of the main verb
  * হওয়া _haoŷā_ (“be, become”) combines with the imperfect participle (also called the infinitive) of the main verb to create a necessitative meaning (“to have to”)
  * চাওয়া _cāoŷā_ (“want”) combines with the infinitive (also called the verbal noun) of the main verb
* There are verb-verb compounds, where the semantically more salient verb comes first in the form
  of a participle, and the semantically less salient verb comes second and has a finite form.
  There is a restricted set of verbs that can occur at the second position of verb-verb compounds.
  Note that these are not considered auxiliary verbs in UD.
  * যাওয়া _yāoŷā_ (“to go”)
  * নেয়া _neŷā_ (“to take”)
  * দেত্তয়া _dettaŷā_ (“to give”)
  * বসা _basā_ (“to sit”)
  * আসা _āsā_ (“to come”)
* There are noun-verb compounds where the noun is the semantically more salient part and it comes first.
  These are treated as light-verb constructions, i.e., the noun is attached to the verb as [compound:lvc]()
  rather than an object. The verb is not treated as auxiliary. Examples:
  * শেষ করা _śeṣa karā_ “to finish” (lit. “end do”)
* There are five main (de)verbal forms, distinguished by the UPOS tag and the value of the [VerbForm]() feature:
  * Infinitive `Inf`, tagged [VERB]() or [AUX](). This is the citation form (lemma) of the verb.
    When used in a nominal position (as a subject of another verb, with a case suffix, with possessive modifiers etc.),
    it is instead tagged [NOUN]() and its `VerbForm` is `Vnoun` (verbal noun) rather than `Inf`.
  * Finite verb `Fin`, tagged [VERB]() or [AUX]().
  * Participle `Part`, tagged [VERB]() or [AUX](). It does not express person.
    The two main types of participles are distinguished by [Aspect](). The third type, conditional participle, is distinguished by [Mood]().
    * Imperfect participle. Some sources (e.g., Wiktionary) may use the term infinitive for this form and verbal noun for what we call infinitive.
    * Perfect participle.
    * Conditional participle: `Mood=Cnd`.

### Nominal Features

* The two main values of the [Number]() feature are `Sing` and `Plur`.
  Nouns ([NOUN]() and [PROPN]()) can inflect for `Number` but the default singular form is usually used unless plural needs to be explicitly signaled.
  For personal pronouns ([PRON]()), both singular and plural forms are used.
  The `Number` of subject (unlike its `Person`) is not cross-referenced by the finite verb.
* [Case]() has up to 4 possible values: `Nom`, `Gen`, `Acc`, `Loc`.
  It occurs with the nominal words, i.e., [NOUN](), [PROPN](), [PRON]().
  The accusative form is also called objective and used in contexts where other languages would use a dative form.
  While the accusative form of personal pronouns is regularly used, for nouns (and especially inanimate nouns), the nominative form is often used also in object position.
* Definite articles can be added in the form of the suffixes টা/টি _-ţa/ţi_ (singular) and গুলো/গুলি _-gulo/guli_ (plural).
  These have [Definite]() value [Def]().

### Degree and Polarity

* [Degree]() applies to adjectives ([ADJ]()) and has one of three possible values: `Pos`, `Cmp`, `Sup`.

### Verbal Features

* [Aspect]() has three values: perfective (`Perf`), imperfective (`Imp`) and habitual (`Hab`)
  The same are available in finite forms, though present continuous (progressive) finite forms 
  will get `Aspect=Prog` rather than `Aspect=Imp`.
* Finite verbs always have one of two values of [Mood](): `Ind` or `Imp`.
  The conditional mood `Cnd` is only used with the conditional participle.
* Finite verbs distinguish the [Person]() of the subject but not its `Number`.
  Infinitives and participles do not distinguish `Person`.
* Verbs in the indicative mood always have one of three values of [Tense](): `Past`, `Pres` or `Fut`.
* There are two values of the [Voice]() feature: `Act` and `Pass`.
* There are three values of the [Polite]() feature: `Form`, `Infm` and `Intm`.

### Pronouns, Determiners, Quantifiers

* [PronType]() is used with pronouns ([PRON]()), determiners ([DET]()) and adverbs ([ADV]()).
* [NumType]() is used with numerals ([NUM]()), adjectives ([ADJ]()), determiners ([DET]()) and adverbs ([ADV]()).
* [Person]() is a lexical feature of personal pronouns ([PRON]()) and has three values, `1`, `2` and `3`.
  Person is not marked on other types of pronouns and on nouns, although they can be almost always interpreted as the 3rd person.
  * As a cross-reference to subject, person is also marked on finite verbs ([VERB](), [AUX]()).
* Personal pronouns also have one of two values of [Number](): `Sing` or `Plur`.
  They are lemmatized to the singular form, i.e., grammatical number is treated as (irregular) inflection.
  Note that the number of subject is not cross-referenced by finite verbs.
* Personal pronouns have up to three [Case]() forms: `Nom` (the base form), `Acc` (the objective form, also used in contexts where other languages use dative), and
  `Gen` (the genitive form).
  * There is no specific category of possessive pronouns. Instead, the genitive form of personal pronouns is used to encode possession.
* [Polite]() is a lexical feature of personal pronouns. It has the values `Form`, `Infm` and `Intm`.
* [Animacy]() is a lexical feature of personal pronouns that determines the declension strategies available.
  It has the values `Anim` and `Inan`.

### Other Features

* There are the following language-specific features:
  * [PartType](): `PartType=Int` (interrogative) marks the word কি _ki_ when it functions as a question particle (rather than the pronoun “what”).
    `PartType=Neg` (negative) marks the negative particles না _nā_, নাই _nāi_ (“not”).

## Syntax

### Core Arguments, Oblique Arguments and Adjuncts

* Nominal subject ([nsubj]()) is a noun phrase in the nominative case, without preposition.
  * An infinitive verb in the subject position is tagged as a verbal [NOUN](), hence it is also labeled [nsubj]().
* Objects may be bare noun phrases in nominative or accusative form.
* Nominals in the locative form, if modifying a verb, are considered oblique ([obl]()).
* In passive clauses, the subject is labeled with [nsubj:pass]().
  * If the demoted agent is present, it has the form of a bare instrumental phrase and its relation is labeled [obl:agent]().

### Non-verbal Clauses

* In the present tense, simple juxtaposition of the subject and the nominal/adjectival predicate is used, without an overt copula.

### Other relations

* Noun classifiers are used in Bengali to count numbers of a noun. 
  For example, "দুই_জন ছাত্র গল্প করছিল" *dul_jon chatro golpo chatril* ("two-CLF person chatting were_doing").
  * If both the classifier and the counted object are present, the classifier 
    (which is tagged as a [NOUN]()), is a [clf]() dependent of the numeral that precedes it.
    The numeral is in turn a [det]() or [nummod]() dependent of what it counts.
  * If only the numeral and the classifier are present, e.g. "দুই_জন গল্প করছিল" *dul_jon golpo chatril*,
    then the classifier is promoted to the head of the nominal phrase, and the numeral is the dependent
    of it with a [det]() or [nummod]() relation.

### Relations Overview

* The following relation subtypes are used in Bengali:
  * [compound:lvc]() for core semantic components of light verb compounds
  * [compound:svc]() for verbs that are part of a serial verb compound
  * [nsubj:pass]() for nominal subjects of passive verbs
  * [csubj:pass]() for clausal subjects of passive verbs
  * [obl:agent]() for agents of passive verbs
  * [acl:relcl]() for relative clauses
  * [nmod:poss]() for possessively used genitive modifiers

## Treebanks

There are [2](../treebanks/bn-comparison.html) Bengali UD treebanks:

  * [Bengali-BRU](../treebanks/bn_bru/index.html)
  * [Bengali-PUD](../treebanks/bn_pud/index.html)
