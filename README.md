## Basic UI Example

``` r
ui <- fluidPage(theme = shinytheme("cerulean"),
                navbarPage(
                  "Shinny Page",
                  
                    tabPanel("Main Tab",
                              sidebarPanel("This is the side"),
                              mainPanel("This is the Main")
                              ),
                    
                    
                    tabPanel("Tab2","In Progress")
                  )
      )
```

``` r
server <- function(input, output) {
  
  output$distPlot <- renderPlot({
    
    
    if(input$SelectPlot =="Jitter"){
      a <- ggplot(iris,aes(x=Sepal.Length,y=Sepal.Width)) + geom_jitter(shape=input$Shape)
    }
    
     if(input$SelectPlot =="Scatter"){
      a <- ggplot(iris,aes(x=Sepal.Length,y=Sepal.Width)) + geom_point(shape=input$Shape)
     }
    
     if(input$SelectPlot =="Line"){
      a <- ggplot(iris,aes(x=Sepal.Length,y=Sepal.Width)) + geom_line(col=input$Shape)
     }
  
    
    a
  })#output$dist
}#Server
```

``` r
shinyApp(ui = ui, server = server)
```

    ## PhantomJS not found. You can install it with webshot::install_phantomjs(). If it is installed, please make sure the phantomjs executable can be found via the PATH variable.

<!--html_preserve-->

<div class="muted well" style="width: 100% ; height: 400px ; text-align: center; box-sizing: border-box; -moz-box-sizing: border-box; -webkit-box-sizing: border-box;">

Shiny applications not supported in static R Markdown documents

</div>

<!--/html_preserve-->
