# imp-lcscraper

langchain colly scraper with impersonation support.

## Credit

Code is copied from [tmc/langchaingo](https://github.com/tmc/langchaingo) since 2025-09-10 with some modifications.

Impersonation support is powered by [imroc/req](https://github.com/imroc/req).

## Install

```
go get github.com/curtisnewbie/imp-lcscraper
```

E.g.,

```go
func Scrape(ctx context.Context, url string) error {
	s, err := impscraper.New(impscraper.WithMaxDepth(2),
		impscraper.WithIgnoreRobotsTxt(true),
		impscraper.WithDelay(50*time.Millisecond),
		impscraper.WithAsync(true),
		impscraper.WithParallelsNum(2),
	)
	if err != nil {
		return err
	}
	pages, log, err := s.Call(ctx, url)
	if err != nil {
		return err
	}
	fmt.Printf("Scraper Log: %v\n", log)
	for _, p := range pages {
		fmt.Printf("%v\n\n", p)
	}
	return nil
}
```
