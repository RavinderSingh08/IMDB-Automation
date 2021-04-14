const pup = require("puppeteer");
const fs = require("fs");
const id = "mijora9576@gmail.com";
const pass = "M1jor@9576"
let tab;

async function main() {
    let browser = await pup.launch({
        headless: false,
        defaultViewport: false,
        args: ['--start-maximized']
    });

    let pages = await browser.pages();
    tab = pages[0];
    await tab.goto("https://www.imdb.com/");
    
    await tab.waitForSelector(".ipc-button.ipc-button--single-padding.ipc-button--center-align-content.ipc-button--default-height.ipc-button--core-baseAlt.ipc-button--theme-baseAlt.ipc-button--on-textPrimary.ipc-text-button.imdb-header__signin-text", { visible: true });
    await tab.click(".ipc-button.ipc-button--single-padding.ipc-button--center-align-content.ipc-button--default-height.ipc-button--core-baseAlt.ipc-button--theme-baseAlt.ipc-button--on-textPrimary.ipc-text-button.imdb-header__signin-text");

    await tab.waitForSelector(".auth-provider-text", { visible: true });
    let signin = await tab.$$(".auth-provider-text");
    await signin[0].click();

    await tab.waitForSelector("#ap_email", { visible: true });
    await tab.type("#ap_email", id);
    await tab.type("#ap_password", pass);
    await tab.click("#signInSubmit");

    await tab.waitForSelector(".ipc-icon.ipc-icon--menu.ipc-button__icon.ipc-button__icon--pre", { visible: true });
    await tab.click(".ipc-icon.ipc-icon--menu.ipc-button__icon.ipc-button__icon--pre");
    await tab.waitForSelector("a[role='menuitem']", { visible: true });
    let selectType = await tab.$$("a[role='menuitem']");
    await selectType[2].click();

    await tab.waitForNavigation({ waitUntil: "networkidle2" });
    let moviesLink = await tab.$$(".lister-list .titleColumn a");
    await moviesLink[0].click();
}

main(); 
