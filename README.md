# Fused effects test

This is a small project to try out the fused effects library

### Build errors

Errors that I get when I try to build this

```
Resolving dependencies...
Build profile: -w ghc-8.6.5 -O1
In order, the following will be built (use -v for more details):
 - fe-test-0.1.0.0 (exe:fe-test) (configuration changed)
Configuring executable 'fe-test' for fe-test-0.1.0.0..
Warning: The 'license-file' field refers to the file 'LICENSE' which does not
exist.
Preprocessing executable 'fe-test' for fe-test-0.1.0.0..
Building executable 'fe-test' for fe-test-0.1.0.0..
[1 of 2] Compiling ReinterpretLog   ( src/ReinterpretLog.hs, /Users/max/dev2/haskell/fe-test/dist-newstyle/build/x86_64-osx/ghc-8.6.5/fe-test-0.1.0.0/x/fe-test/build/fe-test/fe-test-tmp/ReinterpretLog.o )

src/ReinterpretLog.hs:102:3: error:
    • Couldn't match expected type ‘LogStdoutC m a’
                  with actual type ‘(:+:) (Log a10) g2 m6 k2
                                    -> t4 -> LogStdoutC m7 a9’
    • The equation(s) for ‘alg’ have three arguments,
      but its type ‘(:+:) (Log String) sig2 (LogStdoutC m) a
                    -> LogStdoutC m a’
      has only one
      In the instance declaration for
        ‘Algebra (Log String :+: sig) (LogStdoutC m)’
    • Relevant bindings include
        alg :: (:+:) (Log String) sig2 (LogStdoutC m) a -> LogStdoutC m a
          (bound at src/ReinterpretLog.hs:102:3)
    |
102 |   alg hdl sig ctx = case sig of
    |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^...

src/ReinterpretLog.hs:103:24: error:
    • Couldn't match expected type ‘a9’ with actual type ‘t4’
        ‘t4’ is untouchable
          inside the constraints: k2 ~ ()
          bound by a pattern with constructor:
                     Log :: forall a (m :: * -> *). a -> Log a m (),
                   in a case alternative
          at src/ReinterpretLog.hs:103:8-18
    • In the first argument of ‘(<$)’, namely ‘ctx’
      In the expression: ctx <$ liftIO (putStrLn message)
      In a case alternative:
          L (Log message) -> ctx <$ liftIO (putStrLn message)
    • Relevant bindings include
        ctx :: t4 (bound at src/ReinterpretLog.hs:102:15)
    |
103 |     L (Log message) -> ctx <$ liftIO (putStrLn message)
    |                        ^^^

src/ReinterpretLog.hs:103:48: error:
    • Couldn't match expected type ‘String’ with actual type ‘a10’
        ‘a10’ is untouchable
          inside the constraints: k2 ~ ()
          bound by a pattern with constructor:
                     Log :: forall a (m :: * -> *). a -> Log a m (),
                   in a case alternative
          at src/ReinterpretLog.hs:103:8-18
    • In the first argument of ‘putStrLn’, namely ‘message’
      In the first argument of ‘liftIO’, namely ‘(putStrLn message)’
      In the second argument of ‘(<$)’, namely
        ‘liftIO (putStrLn message)’
    • Relevant bindings include
        message :: a10 (bound at src/ReinterpretLog.hs:103:12)
        sig :: (:+:) (Log a10) g2 m6 k2
          (bound at src/ReinterpretLog.hs:102:11)
    |
103 |     L (Log message) -> ctx <$ liftIO (putStrLn message)
    |                                                ^^^^^^^

src/ReinterpretLog.hs:105:41: error:
    • Couldn't match kind ‘*’ with ‘* -> *’
      When matching types
        a8 :: *
        (->) (g2 m6 k2) :: * -> *
      Expected type: Reader (g2 m6 k2) ((->) (g2 m6 k2)) (t4 -> m7 a9)
        Actual type: a8 -> t4 -> m7 a9
    • Probable cause: ‘(.)’ is applied to too few arguments
      In the first argument of ‘alg’, namely ‘(runLogStdout . hdl)’
      In the first argument of ‘LogStdoutC’, namely
        ‘(alg (runLogStdout . hdl) other ctx)’
      In the expression: LogStdoutC (alg (runLogStdout . hdl) other ctx)
    • Relevant bindings include
        other :: g2 m6 k2 (bound at src/ReinterpretLog.hs:105:7)
        sig :: (:+:) (Log a10) g2 m6 k2
          (bound at src/ReinterpretLog.hs:102:11)
    |
105 |     R other         -> LogStdoutC (alg (runLogStdout . hdl) other ctx)
    |                                         ^^^^^^^^^^^^^^^^^^

src/ReinterpretLog.hs:105:56: error:
    • Couldn't match expected type ‘a8 -> LogStdoutC ((->) t4) (m7 a9)’
                  with actual type ‘(:+:) (Log String) sig2 (LogStdoutC m) a’
    • In the second argument of ‘(.)’, namely ‘hdl’
      In the first argument of ‘alg’, namely ‘(runLogStdout . hdl)’
      In the first argument of ‘LogStdoutC’, namely
        ‘(alg (runLogStdout . hdl) other ctx)’
    • Relevant bindings include
        ctx :: t4 (bound at src/ReinterpretLog.hs:102:15)
        hdl :: (:+:) (Log String) sig2 (LogStdoutC m) a
          (bound at src/ReinterpretLog.hs:102:7)
        alg :: (:+:) (Log String) sig2 (LogStdoutC m) a -> LogStdoutC m a
          (bound at src/ReinterpretLog.hs:102:3)
    |
105 |     R other         -> LogStdoutC (alg (runLogStdout . hdl) other ctx)
    |                                                        ^^^

src/ReinterpretLog.hs:121:3: error:
    • Couldn't match expected type ‘ReinterpretLogC s t m a’
                  with actual type ‘(:+:) (Log a7) g1 m4 k1
                                    -> t3 -> ReinterpretLogC s3 t2 m5 a6’
    • The equation(s) for ‘alg’ have three arguments,
      but its type ‘(:+:) (Log s) sig2 (ReinterpretLogC s t m) a
                    -> ReinterpretLogC s t m a’
      has only one
      In the instance declaration for
        ‘Algebra (Log s :+: sig) (ReinterpretLogC s t m)’
    • Relevant bindings include
        alg :: (:+:) (Log s) sig2 (ReinterpretLogC s t m) a
               -> ReinterpretLogC s t m a
          (bound at src/ReinterpretLog.hs:121:3)
    |
121 |   alg hdl sig ctx = ReinterpretLogC $ case sig of
    |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^...

src/ReinterpretLog.hs:124:7: error:
    • Couldn't match expected type ‘a6’ with actual type ‘t3’
        ‘t3’ is untouchable
          inside the constraints: k1 ~ ()
          bound by a pattern with constructor:
                     Log :: forall a (m :: * -> *). a -> Log a m (),
                   in a case alternative
          at src/ReinterpretLog.hs:122:8-12
    • In the first argument of ‘(<$)’, namely ‘ctx’
      In a stmt of a 'do' block: ctx <$ log (f s)
      In the expression:
        do f <- ask @(s -> t)
           ctx <$ log (f s)
    • Relevant bindings include
        ctx :: t3 (bound at src/ReinterpretLog.hs:121:15)
    |
124 |       ctx <$ log (f s)
    |       ^^^

src/ReinterpretLog.hs:124:21: error:
    • Couldn't match expected type ‘s’ with actual type ‘a7’
        ‘a7’ is untouchable
          inside the constraints: k1 ~ ()
          bound by a pattern with constructor:
                     Log :: forall a (m :: * -> *). a -> Log a m (),
                   in a case alternative
          at src/ReinterpretLog.hs:122:8-12
      ‘s’ is a rigid type variable bound by
        the instance declaration
        at src/ReinterpretLog.hs:(116,6)-(119,52)
    • In the first argument of ‘f’, namely ‘s’
      In the first argument of ‘log’, namely ‘(f s)’
      In the second argument of ‘(<$)’, namely ‘log (f s)’
    • Relevant bindings include
        f :: s -> t (bound at src/ReinterpretLog.hs:123:7)
        s :: a7 (bound at src/ReinterpretLog.hs:122:12)
        sig :: (:+:) (Log a7) g1 m4 k1
          (bound at src/ReinterpretLog.hs:121:11)
        hdl :: (:+:) (Log s) sig2 (ReinterpretLogC s t m) a
          (bound at src/ReinterpretLog.hs:121:7)
        alg :: (:+:) (Log s) sig2 (ReinterpretLogC s t m) a
               -> ReinterpretLogC s t m a
          (bound at src/ReinterpretLog.hs:121:3)
    |
124 |       ctx <$ log (f s)
    |                     ^

src/ReinterpretLog.hs:126:18: error:
    • Couldn't match type ‘ReaderC (s2 -> t1) m3 a4’
                     with ‘t3 -> ReaderC (s3 -> t2) m5 a6’
      Expected type: (:+:) f1 g1 m4 k1 -> t3 -> ReaderC (s3 -> t2) m5 a6
        Actual type: (:+:) f1 g1 m4 k1 -> ReaderC (s2 -> t1) m3 a4
    • The function ‘alg’ is applied to three arguments,
      but its type ‘Reader
                      ((:+:) f1 g1 m4 k1)
                      ((->) ((:+:) f1 g1 m4 k1))
                      (ReaderC (s2 -> t1) m3 a4)
                    -> (:+:) f1 g1 m4 k1 -> ReaderC (s2 -> t1) m3 a4’
      has only two
      In the expression: alg (runReinterpretLogC . hdl) (R other) ctx
      In a case alternative:
          R other -> alg (runReinterpretLogC . hdl) (R other) ctx
    • Relevant bindings include
        ctx :: t3 (bound at src/ReinterpretLog.hs:121:15)
    |
126 |     R other   -> alg (runReinterpretLogC . hdl) (R other) ctx
    |                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

src/ReinterpretLog.hs:126:23: error:
    • Couldn't match kind ‘*’ with ‘* -> *’
      When matching types
        a5 :: *
        (->) ((:+:) f1 g1 m4 k1) :: * -> *
      Expected type: Reader
                       ((:+:) f1 g1 m4 k1)
                       ((->) ((:+:) f1 g1 m4 k1))
                       (ReaderC (s2 -> t1) m3 a4)
        Actual type: a5 -> ReaderC (s2 -> t1) m3 a4
    • Probable cause: ‘(.)’ is applied to too few arguments
      In the first argument of ‘alg’, namely ‘(runReinterpretLogC . hdl)’
      In the expression: alg (runReinterpretLogC . hdl) (R other) ctx
      In a case alternative:
          R other -> alg (runReinterpretLogC . hdl) (R other) ctx
    • Relevant bindings include
        other :: g1 m4 k1 (bound at src/ReinterpretLog.hs:126:7)
        sig :: (:+:) (Log a7) g1 m4 k1
          (bound at src/ReinterpretLog.hs:121:11)
    |
126 |     R other   -> alg (runReinterpretLogC . hdl) (R other) ctx
    |                       ^^^^^^^^^^^^^^^^^^^^^^^^

src/ReinterpretLog.hs:126:44: error:
    • Couldn't match expected type ‘a5 -> ReinterpretLogC s2 t1 m3 a4’
                  with actual type ‘(:+:) (Log s) sig2 (ReinterpretLogC s t m) a’
    • In the second argument of ‘(.)’, namely ‘hdl’
      In the first argument of ‘alg’, namely ‘(runReinterpretLogC . hdl)’
      In the expression: alg (runReinterpretLogC . hdl) (R other) ctx
    • Relevant bindings include
        hdl :: (:+:) (Log s) sig2 (ReinterpretLogC s t m) a
          (bound at src/ReinterpretLog.hs:121:7)
        alg :: (:+:) (Log s) sig2 (ReinterpretLogC s t m) a
               -> ReinterpretLogC s t m a
          (bound at src/ReinterpretLog.hs:121:3)
    |
126 |     R other   -> alg (runReinterpretLogC . hdl) (R other) ctx
    |                                            ^^^

src/ReinterpretLog.hs:145:3: error:
    • Couldn't match expected type ‘CollectLogMessagesC s m a’
                  with actual type ‘(:+:) (Log a2) g0 m1 k0
                                    -> t0 -> CollectLogMessagesC s1 m2 a3’
    • The equation(s) for ‘alg’ have three arguments,
      but its type ‘(:+:) (Log s) sig2 (CollectLogMessagesC s m) a
                    -> CollectLogMessagesC s m a’
      has only one
      In the instance declaration for
        ‘Algebra (Log s :+: sig) (CollectLogMessagesC s m)’
    • Relevant bindings include
        alg :: (:+:) (Log s) sig2 (CollectLogMessagesC s m) a
               -> CollectLogMessagesC s m a
          (bound at src/ReinterpretLog.hs:145:3)
    |
145 |   alg hdl sig ctx = CollectLogMessagesC $ case sig of
    |   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^...

src/ReinterpretLog.hs:146:18: error:
    • Couldn't match expected type ‘a3’ with actual type ‘t0’
        ‘t0’ is untouchable
          inside the constraints: k0 ~ ()
          bound by a pattern with constructor:
                     Log :: forall a (m :: * -> *). a -> Log a m (),
                   in a case alternative
          at src/ReinterpretLog.hs:146:8-12
    • In the first argument of ‘(<$)’, namely ‘ctx’
      In the expression: ctx <$ tell [s]
      In a case alternative: L (Log s) -> ctx <$ tell [s]
    • Relevant bindings include
        ctx :: t0 (bound at src/ReinterpretLog.hs:145:15)
    |
146 |     L (Log s) -> ctx <$ tell [s]
    |                  ^^^

src/ReinterpretLog.hs:148:18: error:
    • Couldn't match type ‘WriterC [s0] m0 a0’
                     with ‘t0 -> WriterC [s1] m2 a3’
      Expected type: (:+:) f0 g0 m1 k0 -> t0 -> WriterC [s1] m2 a3
        Actual type: (:+:) f0 g0 m1 k0 -> WriterC [s0] m0 a0
    • The function ‘alg’ is applied to three arguments,
      but its type ‘Reader
                      ((:+:) f0 g0 m1 k0) ((->) ((:+:) f0 g0 m1 k0)) (WriterC [s0] m0 a0)
                    -> (:+:) f0 g0 m1 k0 -> WriterC [s0] m0 a0’
      has only two
      In the expression: alg (runCollectLogMessagesC . hdl) (R other) ctx
      In a case alternative:
          R other -> alg (runCollectLogMessagesC . hdl) (R other) ctx
    • Relevant bindings include
        ctx :: t0 (bound at src/ReinterpretLog.hs:145:15)
    |
148 |     R other   -> alg (runCollectLogMessagesC . hdl) (R other) ctx
    |                  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

src/ReinterpretLog.hs:148:23: error:
    • Couldn't match kind ‘*’ with ‘* -> *’
      When matching types
        a1 :: *
        (->) ((:+:) f0 g0 m1 k0) :: * -> *
      Expected type: Reader
                       ((:+:) f0 g0 m1 k0) ((->) ((:+:) f0 g0 m1 k0)) (WriterC [s0] m0 a0)
        Actual type: a1 -> WriterC [s0] m0 a0
    • Probable cause: ‘(.)’ is applied to too few arguments
      In the first argument of ‘alg’, namely
        ‘(runCollectLogMessagesC . hdl)’
      In the expression: alg (runCollectLogMessagesC . hdl) (R other) ctx
      In a case alternative:
          R other -> alg (runCollectLogMessagesC . hdl) (R other) ctx
    • Relevant bindings include
        other :: g0 m1 k0 (bound at src/ReinterpretLog.hs:148:7)
        sig :: (:+:) (Log a2) g0 m1 k0
          (bound at src/ReinterpretLog.hs:145:11)
    |
148 |     R other   -> alg (runCollectLogMessagesC . hdl) (R other) ctx
    |                       ^^^^^^^^^^^^^^^^^^^^^^^^^^^^

src/ReinterpretLog.hs:148:48: error:
    • Couldn't match expected type ‘a1 -> CollectLogMessagesC s0 m0 a0’
                  with actual type ‘(:+:) (Log s) sig2 (CollectLogMessagesC s m) a’
    • In the second argument of ‘(.)’, namely ‘hdl’
      In the first argument of ‘alg’, namely
        ‘(runCollectLogMessagesC . hdl)’
      In the expression: alg (runCollectLogMessagesC . hdl) (R other) ctx
    • Relevant bindings include
        hdl :: (:+:) (Log s) sig2 (CollectLogMessagesC s m) a
          (bound at src/ReinterpretLog.hs:145:7)
        alg :: (:+:) (Log s) sig2 (CollectLogMessagesC s m) a
               -> CollectLogMessagesC s m a
          (bound at src/ReinterpretLog.hs:145:3)
    |
148 |     R other   -> alg (runCollectLogMessagesC . hdl) (R other) ctx
    |

```
