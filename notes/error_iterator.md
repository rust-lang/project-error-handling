# pulse
2019 Feb 16 - 2019 Dec 13

Git Issues

- https://github.com/rust-lang/rust/issues/58520
- https://github.com/rust-lang/rust/pull/58289
    
Discord
Zulip

SO

- https://www.reddit.com/r/rust/comments/aj3lpg/is_an_iterator_impl_over_errorsource_possible/
    
Long Form

# people
haraldh, TimDiekmann, sfackler, Centril, withoutboats, faern, derekdreery,
BurntSushi, teiesti, ehuss, shepmaster, tmandry, JohnTitor, joshtriplett,
ArekPiekarz, JelteF, Aranvion, bbqsrc, Dylan-DPC, KodrAus

# tl;dr
Question was asked: is an iterator `impl` over `Error::source()` possible?

# grok
```{rust}
use std::error::Error;

struct SourceIter<'a> {
  current: Option<&'a (dyn Error + 'static)>,
}

impl<'a> Iterator for SourceIter<'a> {
  type Item = &'a (dyn Error + 'static);
  
  fn next(&mut self) -> Option<Self::Item> {
    let current = self.current;
    self.current = self.current.and_then(Error::source);
    current
  }
}

fn source_iter(error : &impl Error) -> impl Iterator<Item = &(dyn Error + 'static)> {
  SourceIter {
    current : error.source(),
  }
}

```

```{rust}
let next_error_type_a = err
  .iter()
  .filter_map(Error::downcast_ref::<ErrorTypeA>)
  .next();
    
let source_root_error = err.iter().last();
```

# misc
## haraldh
- 
