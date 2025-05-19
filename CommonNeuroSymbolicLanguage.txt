<requesting_system> ::= <needs> | <goal> | <planning> | <execution> | <command> | <gui> | <observability> | <state_curation> | <rag> 
<variable> ::= [A-Z] (":" <type>)? | [A-Z] "(" <term_list> ")" (":" <type>)?
<constant> ::= [a-z] (":" <type>)? | [a-z] "(" <term_list> ")" (":" <type>)?
<type> ::= [A-Z][a-zA-Z0-9_]* | <type> "→" <type> | <type> "[" <term> "]" | <type> "<" <type> ">" | <type> "*" <type> | "Set" "<" <type> ">" | "Prop" | "Type" | <type> "(" <term> ")" | <type> "|" <constraint_expr>
<function> ::= <func_name> "(" <term_list> ")" (":" <type>)? | "λ" <binder_list> "." <term>
<func_name> ::= [a-zA-Z_][a-zA-Z0-9_]*
<binder_list> ::= <binder> | <binder> "," <binder_list>
<binder> ::= <variable> | "(" <variable> ":" <type> ")" | "[" <variable> ":" <type> "]"
<term> ::= <variable> | <constant> | <function> | <predicate> | <arithmetic_expr> | <lambda> | <let_binding> | <pattern_match> | <external_ref>
<term_list> ::= <term> | <term> "," <term_list>
<predicate> ::= <pred_name> "(" <term_list> ")" (":" <type>)? | <pred_name> "[" <predicate_list> "]" (":" <type>)?
<pred_name> ::= [A-Z][a-zA-Z0-9_]* | <user_op>
<formula> ::= <predicate>
           | "(" <formula> ")"
           | <formula> "∧" <formula>
           | <formula> "∨" <formula>
           | "¬" <formula>
           | <formula> "→" <formula>
           | <formula> "↔" <formula>
           | "∀" <binder_list> "." <formula>
           | "∃" <binder_list> "." <formula>
           | "Π" <binder_list> "." <formula>
           | "Σ" <binder_list> "." <formula>
           | "∀" <type_var> ":" <type> "." <formula>
           | "∃" <type_var> ":" <type> "." <formula>
           | "□" <formula>
           | "◇" <formula>
           | "O" <formula>
           | "P" <formula>
           | "F" <interval_expr> "(" <formula> ")"
           | "G" <interval_expr> "(" <formula> ")"
           | "X" <formula>
           | <formula> "U" <interval_expr> <formula>
           | <formula> "S" <interval_expr> <formula>
           | <formula> "⇒" <formula>
           | <formula> "~>" <formula>
           | "Pr(" <formula> ")=" <prob_domain>
           | "Poss(" <formula> ")=" <poss_domain>
           | "Fuzzy(" <formula> ")=" <fuzzy_domain>
           | "Dist(" <formula> ")=" <distribution>
           | "Bayes(" <formula> "|" <formula> ")"
           | "Ind(" <formula> "," <evidence> ")"
           | "[If " <formula> " then " <formula> "]"
           | "K_" <agent> "(" <formula> ")"
           | "B_" <agent> "(" <formula> ")"
           | "I_" <agent> "(" <formula> ")"
           | "N(" <formula> ")"
           | "V(" <formula> ")"
           | "Step_" <number> "(" <formula> ")"
           | "Seq(" <formula_list> ")"
           | "Search(" <goal> "," <constraints> ")"
           | "Model(" <model_name> "," <formula> ")"
           | "Explains(" <formula> "," <formula> ["," <justification>] ")"
           | "Justifies(" <formula> "," <formula> ")"
           | "Design(" <experiment> "," <hypothesis> ")"
           | "Before(" <term> "," <term> ["," <region>] ")"
           | "After(" <term> "," <term> ["," <region>] ")"
           | "During(" <term> "," <term> ["," <region>] ")"
           | "Struct(" <formula> ")"
           | "Map(" <formula> "," <formula> ")"
           | "Default(" <formula> "," <exceptions> ")"
           | "¬_def(" <formula> ")"
           | "Meta(" <meta_op> "," <formula> ")"
           | "Context[" <context_tag> "](" <formula> ")"
           | <user_op> "(" <formula_list> ")"
           | "Macro(" <macro_name> "," <macro_body> ")"
           | "Ref(" <formula> ")"
           | "QuantFormula(" <formula_var> "." <formula> ")"
           | "Let " <binder_list> "=" <term> "in" <formula>
           | "λ" <binder_list> "." <formula>
           | "match " <term> "with" <pattern_cases>
           | "!" <formula> | "?" <formula>
           | <formula> "*" <formula> | <formula> "⊗" <formula>
           | <formula> "&" <formula> | <formula> "⅋" <formula>
           | <formula> "-" <formula>
           | <formula> "|" <formula>
           | <formula> "⊸" <formula>
           | "⟨" <proof_term> "⟩"
           | "Quote(" <formula> ")"
           | "Reflect(" <formula> ")"
           | "External(" <external_ref> ")"
           | "Ontology(" <ontology_ref> ")"
           | "Resource(" <resource_tag> "," <formula> ")"
           | "Sequent(" <context> "⊢" <formula> ")"
           | "Derivation(" <proof_term> ")"
           | "Spatial(" <spatial_expr> ")"
           | "Process(" <process_expr> ")"
           | "Arith(" <arithmetic_expr> ")"
           | "Poly(" <polynomial_expr> ")"
           | "Ineq(" <inequality_expr> ")"
           | "Sort(" <sort_expr> ")"
           | "Polymorphic(" <type_var> "," <formula> ")"
           | "Bind(" <binder_list> "," <formula> ")"
           | "Scoped(" <scope_tag> "," <formula> ")"
           | "Pattern(" <pattern_expr> ")"
           | "Proof(" <proof_term> ")"
           | "Construct(" <formula_expr> ")"
           | "Eval(" <formula_expr> ")"
           | "With(" <formula> "," <context> ")"
           | "ExistsUnique(" <binder_list> "." <formula> ")"
           | "ForallUnique(" <binder_list> "." <formula> ")"
           | "Min(" <arithmetic_expr> "," <formula> ")"
           | "Max(" <arithmetic_expr> "," <formula> ")"
           | "Sum(" <arithmetic_expr> "," <formula> ")"
           | "Product(" <arithmetic_expr> "," <formula> ")"
           | "IntervalRel(" <interval_rel_expr> "," <formula> ")"
           | "SpatialRel(" <spatial_rel_expr> "," <formula> ")"
           | "TemporalRel(" <temporal_rel_expr> "," <formula> ")"
           | "Database(" <db_ref> "," <query_expr> ")"
           | "KG(" <kg_ref> "," <kg_query_expr> ")"
           | "Transformer(" <transformer_name> "," <input_data> ["," <transformer_task>] ")" (":" <type>)?
<type_var> ::= [A-Z][a-zA-Z0-9_]*
<prob_domain> ::= <prob_value> | <prob_interval> | <prob_distribution>
<poss_domain> ::= <poss_value> | <poss_interval> | <poss_measure>
<fuzzy_domain> ::= <fuzzy_value> | <fuzzy_interval> | <fuzzy_measure>
<prob_value> ::= [0-1](\.[0-9]+)?
<poss_value> ::= [0-1](\.[0-9]+)?
<fuzzy_value> ::= [0-1](\.[0-9]+)?
<prob_interval> ::= "[" <prob_value> "," <prob_value> "]"
<poss_interval> ::= "[" <poss_value> "," <poss_value> "]"
<fuzzy_interval> ::= "[" <fuzzy_value> "," <fuzzy_value> "]"
<prob_distribution> ::= <distribution>
<poss_measure> ::= <measure_expr>
<fuzzy_measure> ::= <measure_expr>
<distribution> ::= <dist_name> "(" <dist_params> ")"
<dist_name> ::= [A-Z][a-zA-Z0-9_]*
<dist_params> ::= <arithmetic_expr> | <arithmetic_expr> "," <dist_params>
<measure_expr> ::= <arithmetic_expr> | <arithmetic_expr> "," <measure_expr>
<agent> ::= [a-z][a-zA-Z0-9_]*
<number> ::= [0-9]+
<formula_list> ::= <formula> | <formula> "," <formula_list>
<goal> ::= <formula>
<constraints> ::= <formula_list> | <constraint_expr>
<model_name> ::= [A-Z][a-zA-Z0-9_]*
<evidence> ::= <formula_list>
<experiment> ::= <term>
<hypothesis> ::= <formula>
<interval> ::= "[" <number> "," <number> "]"
<interval_expr> ::= <interval> | <arithmetic_expr> | <interval_rel_expr>
<interval_rel_expr> ::= <interval> | <interval> "," <interval_rel_expr> | <interval_rel_op> "(" <interval> "," <interval> ")"
<interval_rel_op> ::= "Meets" | "Overlaps" | "Starts" | "Finishes" | "During" | "Equals" | "Before" | "After"
<region> ::= [a-zA-Z0-9_]+
<exceptions> ::= <formula_list>
<justification> ::= <formula>
<meta_op> ::= "Provable" | "Consistent" | "Equivalent" | "Entails" | "Refutable" | "Admissible"
<context_tag> ::= [a-zA-Z0-9_]+
<user_op> ::= [A-Z][a-zA-Z0-9_]+
<macro_name> ::= [A-Z][a-zA-Z0-9_]*
<macro_body> ::= <formula>
<formula_var> ::= [A-Z][a-zA-Z0-9_]*
<arithmetic_expr> ::= <number> | <arithmetic_expr> "+" <arithmetic_expr> | <arithmetic_expr> "-" <arithmetic_expr> | <arithmetic_expr> "*" <arithmetic_expr> | <arithmetic_expr> "/" <arithmetic_expr> | "(" <arithmetic_expr> ")" | <variable> | <function>
<polynomial_expr> ::= <arithmetic_expr> | <arithmetic_expr> "^" <number> | <polynomial_expr> "+" <polynomial_expr>
<inequality_expr> ::= <arithmetic_expr> "<" <arithmetic_expr> | <arithmetic_expr> "≤" <arithmetic_expr> | <arithmetic_expr> ">" <arithmetic_expr> | <arithmetic_expr> "≥" <arithmetic_expr> | <arithmetic_expr> "=" <arithmetic_expr>
<sort_expr> ::= <type> | <type> "<:" <type> | <type> "∧" <type> | <type> "∨" <type>
<spatial_expr> ::= <spatial_rel_expr> | <spatial_op> "(" <spatial_args> ")"
<spatial_rel_expr> ::= <spatial_op> "(" <spatial_args> ")"
<spatial_op> ::= "Adjacent" | "Inside" | "Contains" | "Disjoint" | "Touches" | "Overlaps"
<spatial_args> ::= <term> | <term> "," <spatial_args>
<process_expr> ::= <process_op> "(" <process_args> ")"
<process_op> ::= "Par" | "Seq" | "Choice" | "Restrict" | "Comm" | "Replicate"
<process_args> ::= <term> | <term> "," <process_args>
<pattern_cases> ::= <pattern_case> | <pattern_case> "|" <pattern_cases>
<pattern_case> ::= <pattern_expr> "→" <formula>
<pattern_expr> ::= <term> | <term> ":" <type> | <pattern_expr> "," <pattern_expr>
<lambda> ::= "λ" <binder_list> "." <term>
<let_binding> ::= "let" <binder_list> "=" <term> "in" <term>
<external_ref> ::= "ext:" <external_id>
<external_id> ::= [a-zA-Z0-9_:./#-]+
<ontology_ref> ::= "ont:" <ontology_id>
<ontology_id> ::= [a-zA-Z0-9_:./#-]+
<resource_tag> ::= [a-zA-Z0-9_]+
<context> ::= <formula_list> | <resource_tag> | <context_tag>
<proof_term> ::= <proof_var> | <proof_const> | <proof_app> | <proof_abs> | <proof_pair> | <proof_case> | <proof_seq> | <proof_ref> | <proof_let>
<proof_var> ::= [p][a-zA-Z0-9_]*
<proof_const> ::= [P][a-zA-Z0-9_]*
<proof_app> ::= <proof_term> <proof_term>
<proof_abs> ::= "λ" <binder_list> "." <proof_term>
<proof_pair> ::= "(" <proof_term> "," <proof_term> ")"
<proof_case> ::= "case" <proof_term> "of" <pattern_cases>
<proof_seq> ::= <proof_term> ";" <proof_term>
<proof_ref> ::= "ref:" <proof_id>
<proof_id> ::= [a-zA-Z0-9_:./#-]+
<proof_let> ::= "let" <binder_list> "=" <proof_term> "in" <proof_term>
<formula_expr> ::= <formula> | <formula_expr> "," <formula_expr>
<scope_tag> ::= [a-zA-Z0-9_]+
<db_ref> ::= [a-zA-Z0-9_:./#-]+
<query_expr> ::= [a-zA-Z0-9_(),=<>!&|]+
<kg_ref> ::= [a-zA-Z0-9_:./#-]+
<kg_query_expr> ::= [a-zA-Z0-9_(),=<>!&|]+
<constraint_expr> ::= <inequality_expr> | <arithmetic_expr> "=" <arithmetic_expr> | <arithmetic_expr> "<=" <arithmetic_expr> | <arithmetic_expr> ">=" <arithmetic_expr> | <arithmetic_expr> "<" <arithmetic_expr> | <arithmetic_expr> ">" <arithmetic_expr> | <constraint_expr> "∧" <constraint_expr> | <constraint_expr> "∨" <constraint_expr>
<temporal_rel_expr> ::= <interval_rel_op> "(" <interval> "," <interval> ")" | <temporal_rel_expr> "," <temporal_rel_expr>
<kg_query_expr> ::= [a-zA-Z0-9_(),=<>!&|]+
<transformer_name> ::= [A-Z][a-zA-Z0-9_]+
<input_data> ::= <term> | <formula> | <term_list> | <formula_list>
<transformer_task> ::= EnumerativeInduction | StatisticalInduction | TransductiveReasoning | SurfaceAnalogy | MetaphoricalReasoning | IntuitiveReasoning | PatternBasedReasoning | RuleOfThumbReasoning | TheoryOfMind | JointIntentionality | MoralIntuitionism | DivergentThinking | LateralThinking | NarrativeReasoning | TemporalLogic | SpatialLogic | DefeasibleReasoning | DefaultReasoning | BayesianProbabilistic | Retroduction | InferenceToBestExplanation | ExperimentalDesignReasoning | ModelBasedReasoning | StructuralAnalogy | NormativeReasoning | InstrumentalReasoning | HypotheticalReasoning | SubjunctiveReasoning | ChronologicalReasoning | StepByStepProblemSolving | SearchBasedReasoning
